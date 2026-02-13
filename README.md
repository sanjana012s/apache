# Sanjana Local Development Project

A powerful local web development environment with custom domain name resolution and XAMPP-based localhost hosting.

## 🚀 Quick Start

Access your project at `http://sanjana.local` after completing the setup below.

### Project Screenshot

![Sanjana Local Project](images/Screenshot%202026-02-13%20224846.png)

---

## 📋 Prerequisites

- **XAMPP** (Apache, MySQL, PHP) - [Download XAMPP](https://www.apachefriends.org/)
- **Windows OS** (with Admin access)
- **Code Editor** (VS Code, Sublime Text, etc.)
- **Modern Web Browser** (Chrome, Firefox, Edge)

---

## 🔧 Setup Instructions

### Step 1: Install XAMPP

1. Download XAMPP from the official website
2. Run the installer and select:
   - ✅ Apache
   - ✅ MySQL
   - ✅ PHP
   - ✅ phpMyAdmin
3. Choose installation path (default: `C:\xampp`)
4. Complete the installation

### Step 2: Configure DNS - sanjana.local

To access your project via `sanjana.local`, configure your Windows hosts file:

#### **Windows 10/11:**

1. Open **Notepad as Administrator**
   - Press `Win + R`
   - Type `notepad`
   - Right-click → "Run as Administrator"

2. Open the hosts file:
   - Go to `File → Open`
   - Navigate to: `C:\Windows\System32\drivers\etc\`
   - Change file type filter to "All Files (*.*)"
   - Select `hosts` file

3. Add this line at the end:
   ```
   127.0.0.1       sanjana.local
   ```

4. Save and close (Ctrl+S)

5. **Flush DNS Cache** (to apply changes):
   - Open PowerShell as Administrator
   - Run this command:
   ```powershell
   ipconfig /flushdns
   ```

### Step 3: Configure Apache Virtual Host (Optional but Recommended)

For better control, configure XAMPP's Apache:

1. Navigate to: `C:\xampp\apache\conf\extra\`
2. Open `httpd-vhosts.conf` in your editor
3. Add this configuration at the end:

```apache
<VirtualHost *:80>
    ServerName sanjana.local
    ServerAlias www.sanjana.local
    DocumentRoot "C:/xampp/htdocs/sanjana"
    
    <Directory "C:/xampp/htdocs/sanjana">
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>
    
    ErrorLog "logs/sanjana_error.log"
    CustomLog "logs/sanjana_access.log" combined
</VirtualHost>
```

4. Restart Apache in XAMPP Control Panel

---

## 🌐 Running the Project

### Start XAMPP Server

1. **Launch XAMPP Control Panel**
   - Default location: `C:\xampp\xampp-control.exe`

2. **Start Services:**
   - Click **Start** next to `Apache`
   - Click **Start** next to `MySQL` (if using database)

3. **Verify Status:**
   - Green checkmarks = Services running ✓

### Access Your Project

**Option 1: Using Custom Domain**
```
http://sanjana.local
```

**Option 2: Using Localhost**
```
http://localhost/sanjana
```

**Option 3: Using IP Address**
```
http://127.0.0.1/sanjana
```


## 💻 Development Workflow

### 1. **Edit Files**
   - All project files are in: `C:\xampp\htdocs\sanjana\`
   - Edit files with your preferred editor
   - Changes are reflected immediately (no build step needed)

### 2. **View Changes**
   - Refresh your browser (F5 or Ctrl+R)
   - Changes appear instantly

### 3. **Debug**
   - Open **Developer Tools** (F12)
   - Check Console, Network, and Elements tabs
   - Use browser DevTools for debugging

---

## 🐛 Troubleshooting

### Issue: "sanjana.local" not resolving

**Solution:**
1. Verify hosts file entry:
   ```powershell
   Get-Content C:\Windows\System32\drivers\etc\hosts | findstr sanjana
   ```
   Should show: `127.0.0.1 sanjana.local`

2. Flush DNS cache again:
   ```powershell
   ipconfig /flushdns
   ```

3. Clear browser cache (Ctrl+Shift+Delete)

### Issue: Apache won't start in XAMPP

**Solution:**
- Port 80 might be in use
- Check if another service is using it:
  ```powershell
  netstat -ano | findstr :80
  ```
- Change Apache port in `httpd.conf` (C:\xampp\apache\conf\)
- Search for `Listen 80` and change to `Listen 8080`

### Issue: "Permission Denied" errors

**Solution:**
- Run XAMPP Control Panel as Administrator
- Check folder permissions for `C:\xampp\htdocs\sanjana\`

### Issue: Database not connecting (if using MySQL)

**Solution:**
- Start MySQL from XAMPP Control Panel
- Check credentials in your PHP config
- Default: hostname=`localhost`, user=`root`, password=`` (blank)

---

## 🛠️ Advanced Configuration

### Enable HTTPS (SSL)

For HTTPS with self-signed certificate:
1. Generate certificate using OpenSSL (included in XAMPP)
2. Configure SSL in `httpd-ssl.conf`
3. Access via: `https://sanjana.local`

### Use Different Port

1. Edit `C:\xampp\apache\conf\httpd.conf`
2. Find and change: `Listen 80` → `Listen 8080`
3. Restart Apache
4. Access via: `http://sanjana.local:8080`

### Enable PHP Extensions

1. Edit `C:\xampp\php\php.ini`
2. Uncomment needed extensions (remove `;`)
3. Restart Apache

---

## 📚 Useful Resources

- [XAMPP Documentation](https://www.apachefriends.org/docs.html)
- [Apache Configuration](https://httpd.apache.org/docs/)
- [PHP Manual](https://www.php.net/manual/)
- [MDN Web Docs](https://developer.mozilla.org/)

---

## 🎯 Next Steps

1. ✅ Complete the setup above
2. ✅ Verify you can access `http://sanjana.local`
3. ✅ Start editing your HTML/CSS/JavaScript
4. ✅ Build your project!

---

## 📝 Notes

- Keep XAMPP running while developing
- Backup your files regularly
- The project folder is: `C:\xampp\htdocs\sanjana\`
- All changes are live (no compilation needed for HTML/CSS/JS)

---

**Happy coding! 🚀**
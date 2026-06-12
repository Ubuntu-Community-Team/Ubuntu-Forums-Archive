---
title: "Viewing system info inside Ubunutu?"
date: 2009-02-27
forum: General Help
---

### Post by ltHank on 2009-02-27
Is there a menu/window/whatever to view system information inside ubunutu?  As in show I'm running what version, how much memory, that sort of thing...

---

### Post by taurus on 2009-02-27
Applications -> Accessories -> Terminal
```
lsb_release -a
df -h
free -m 
top
```

---

### Post by albandy on 2009-02-27
System --> Administration --> System Monitor

(maybe your menu is different because I'm translating mine directly from spanish)
Sistema --> Administracion --> Monitor del sistema

---

### Post by ltHank on 2009-02-27
Cool, thanks guys!

---

### Post by Therion on 2009-02-27
If you want something along the lines of the "Device Manager" like that other operating system has you can have it by installing the **gnome-device-manager** package from the repo.  It's a very handy tool actually.  Find the menu item under Applications/System Tools once it's installed.

For information overload, click on View/Device Properties in the program window.  This adds a "Properties" tab to the display that lets you really drill down into specifics.

---

### Post by mb_webguy on 2009-02-27
SysInfo ("sudo apt-get install sysinfo") is also very useful.

---


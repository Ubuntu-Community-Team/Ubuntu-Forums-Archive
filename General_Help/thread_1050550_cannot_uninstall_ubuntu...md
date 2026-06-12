---
title: "cannot uninstall ubuntu.."
date: 2009-01-25
forum: General Help
---

### Post by christopherm on 2009-01-25
I can't seem to uninstall ubuntu. 

When I go to "Add or remove Programs" and click on Ubuntu's "uninstall" button nothing happens..

Same thing when I run Uninstall-Ubuntu.exe..

Please help.

---

### Post by christopherm on 2009-01-25
I'm running Ubuntu 8.04.1, dual boot on Winx XP.

---

### Post by brandon88tube on 2009-01-26
You can manually remove it. To do this, delete the ubuntu folder, wubildr, wubildr.mbr and lastly edit your boot.ini file getting rid of the line containing the wubildr.mbr path. Also, get rid of the boot options /noexecute and /usepmtimer. Here is an example of what your boot.ini should look like if you had XP Pro.```
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
```

---


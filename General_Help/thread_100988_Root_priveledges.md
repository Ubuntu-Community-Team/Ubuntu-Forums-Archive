---
title: "Root priveledges"
date: 2005-12-08
forum: General Help
---

### Post by Donnut on 2005-12-08
Is there anyway to give yourself root priveledges in the GUI for a short time?  I know logging in under root is a bad idea but....

---

### Post by Bachstelze on 2005-12-08
what exatly do you want to do as root ?

---

### Post by Donnut on 2005-12-08
would like to copy files to my NTFS hard drive using the GUI instead of terminal.

---

### Post by towsonu2003 on 2005-12-08
```
sudo nautilus
``` will open nautilus (file manager) with root privileges (RISKY)... but I believe ntfs writing isn't supported in ubuntu. you'll need a FAT32 filesystem to share files btw windows and linux...

---

### Post by RAOF on 2005-12-08
Copy files **to** your NTFS drive?  The NTFS kernel module is not a safe way of writing to an ntfs drive (which is why it's read-only by default).  If you already know this, and have some alternative NTFS access system (like the captive ntfs drivers, or something), you could just mount your ntfs drive with write privs.

To get a root nautilus (the file browser) window, you can just run "sudo nautilus" from a console, or "gksudo nautilus" from a script/run application.

---

### Post by Donnut on 2005-12-08
OK, thanks.

---

### Post by RobertLos on 2005-12-09
An even saver way to copy files to your NTFS partition is by copying the files FROM your linux environment while working in Windows using explore2fs
You can easily google this up.

Robert

---

### Post by lcg on 2005-12-09
[QUOTE=RobertLos]An even saver way to copy files to your NTFS partition is by copying the files FROM your linux environment while working in Windows using explore2fs[/QUOTE]
It is easy. However, it only works if you're using ext2 or ext3 for Ubuntu.

Lars

---


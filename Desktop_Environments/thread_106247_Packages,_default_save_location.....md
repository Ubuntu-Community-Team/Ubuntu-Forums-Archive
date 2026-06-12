---
title: "Packages, default save location...."
date: 2005-12-20
forum: Desktop Environments
---

### Post by shirike on 2005-12-20
I have a gamut of questions

1) After downloading packages (e.g. the logitech applet from [http://ubuntuforums.org/showthread.php?t=4357](http://ubuntuforums.org/showthread.php?t=4357)) they are saved to my home directory - do they have to stay there or can I delete them? 

2) After installing the logitech applet, I deleted the file to Wastebasket...and now I can't delete it because I'm chris not root :(

3) Folder names with spaces...causing all sorts of problems. Any way to avoid it or do I need to enable something? Is my home directory meant to be like My documents in Windows?

4) Is there any way I can access my Windows (NTFS) partitions? I have 2x 36GB WD Raptors. 1 is split into 6 partitions - Games (NTFS), Backups (NTFS), Page (NTFS), Linux + Linux Page and 2nd drive is for Windows installation.

any hints/tips for a long-term Windows users for getting settled into Linux would be nice :)

---

### Post by 23meg on 2005-12-20
1) Once you've installed them, you can delete them.

2) Permissions issue. Do "gksudo nautilus", type "trash:///" into the address and see if you can delete the files in there.

3) Yes, it's meant to be like that, the place where you keep your personal stuff. If you mean leading spaces, avoid them; they'll cause a mess with some filesystems. If not, specify what exactly the problems are.

4)  [http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2514926](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2514926)

---


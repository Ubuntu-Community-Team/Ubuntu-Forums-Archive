---
title: "KWIN help please"
date: 2010-09-28
forum: Desktop Environments
---

### Post by popppppz on 2010-09-28
i made a start up entry in sessions manager or start up manager (i forgot the same) called          kwin --replace &         i did this to try to auto start kwin at ubuntu startup to avoid running the default for ubuntu,.....needless to say now i boot into grub so please help me, all i have to work with is a live cd thats 9.04 and the grub menu the system im trying to fix is ubuntu 10.04 thank you

---

### Post by ankspo71 on 2010-09-28
Hi,
If you were in the Gnome desktop when you created the "kwin --replace" autostart entry, boot into your live cd and browse to this folder on your hard drive.
/home/yourname/.config/autostart/

If you were using the KDE desktop when you created the "kwin --replace" autostart entry, it is probably located in this directory on your hard drive.
/home/yourname/.kde/Autostart/

It's best to check both folders to be sure anyways.

Delete the "kwin --replace"  file that you created. Restart your computer and try to boot into the Ubuntu on your hard drive.

If you still have a problem with Grub, it can be repaired too.
[http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html)
[http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html](http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html)
 
Hope this helps.

---

### Post by popppppz on 2010-09-29
thanks, i dont know how to access that folder using the live cd, i tried nautilius but it wont load, and all folders on live cd arent my old folders and files

---

### Post by ankspo71 on 2010-09-29
Hi,
I think this is because you went into the home folder on the live cd and not the other home folder on the hard drive.

When you boot into your live cd, look inside the places menu for an entry mamed "xxx GB File System" or something similar (see image below). One of those would be your hard drive. Click on that and it will mount your hard drive. A file browser window should automatically open up. Now you can browse to: 
```
/home/username/.config/autostart/ 
and if possible...
/home/username/.kde/Autostart/
```
Be sure you replace the "username" with your actual username on your installed Ubuntu. The folders that start with a "." are hidden folders, so you will have to unhide them by pressing Ctrl + H.

[IMG]https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=AttachFile&do=get&target=Screenshot-Mount_Disk.png[/IMG]

---

### Post by popppppz on 2010-09-29
thanks, im triple booting xp win 7 and linux, it shows my xp partition and win7 but not ubuntu, i tried using a super grub disk to fix it but that didnt work, im thinking grub lost the location to my linux kernal? maybe i could mount my linux partition or some how redirect grub to the kernal? i have no idea how to do these things though or if that would even work. also if its possible to redirect with a super grub disk i dont know how to use the super grub either, i just tried to auto fix it and it failed says error 15 which i believe is "cant find kernal location"

---


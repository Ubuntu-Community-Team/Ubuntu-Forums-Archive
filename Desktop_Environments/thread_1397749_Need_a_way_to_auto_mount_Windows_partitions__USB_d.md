---
title: "Need a way to auto mount Windows partitions / USB drives"
date: 2010-02-03
forum: Desktop Environments
---

### Post by 18wheeler on 2010-02-03
Normaly ubuntu would have it figured out for you. but in my situation, because of the intel graphics card problem (thread: [http://ubuntuforums.org/showthread.php?p=8769817#post87698179](http://ubuntuforums.org/showthread.php?p=8769817#post87698179)), I have to use a workaround which involves manual X server start.
 
I avoid X windoe freezes by using 'startx' instead of 'gdm start' to start x windows after log in recovery mode. it mostly works for me, but I cannot easily access to the windows partition or the USB drives anymore.
 
they show up in the browser, but when I click on it, a warning message says it is Unable to mount, Not Authorized. same thing when I plug in a usb HD or flash.
 
Any workaround for this?
 
thanks!

---

### Post by Leppie on 2010-02-04
remove the entries for ntfs partitions from fstab, or better: comment them out
put yourself into the fuse group:
```
sudo adduser <username> fuse
```
install ntfs-confign (you have to be in an x session though):
```
sudo apt-get install ntfs-config
```
you should now have access to ntfs partitions and usb sticks

---

### Post by 666f6f on 2010-04-19
This post may help too [http://ubuntuforums.org/showthread.php?p=9146247#post9146247](http://ubuntuforums.org/showthread.php?p=9146247#post9146247)

---


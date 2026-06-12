---
title: "Mass storage mounting in Dapper???"
date: 2006-06-20
forum: Desktop Environments
---

### Post by smilelover on 2006-06-20
:confused: Hey, guys, is this some kind of joke? Why users can not mount mass storage devices (flash, mp3 player)??? Is there a way to have mass storage things mounted with ordinary user account? Or do I have to edit fstab manually? (no problemo for me, but it's ridiculous when a distro that we want to be a Windows alternative does this...)

---

### Post by Kouya on 2006-06-20
erm what exactly is the problem you are having? I can mount my flash drive as well as my mp3 player.

---

### Post by coolclassic on 2006-06-20
This seems to be an issue with Dapper, go to this thread it hellped me get back usb mounting.

[http://ubuntuforums.org/showthread.php?t=184786&highlight=usbmount](http://ubuntuforums.org/showthread.php?t=184786&highlight=usbmount)

---

### Post by smilelover on 2006-06-21
When I looked into fstab, I found ```
/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
```
I changed umask to 770 and everything works.

I'm thinking about filing a bug...

---


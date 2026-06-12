---
title: "Recovering files from failed Wubi"
date: 2009-06-19
forum: General Help
---

### Post by valikor on 2009-06-19
Hi,

My Wubi installation stopped booting, so I followed the instructions here [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) to access my files.

I'm running ubuntu through a live CD, and mounted my HD.

However, many of my files (perhaps the majority?) are now for one reason or another inaccessible. While trying to open pictures (almost all of them), I get an error "Failed to open input stream for file"

Opening another file, I get "Opening '/vdisk/home/david/Desktop/untitled folder/100_2255.JPG' failed: Permission denied"

In fact, it seems that all of the subfolders in my Documents folder cannot be opened because I don't have the correct permissions. 

How can I correct this? Is there anything I can do?

Thanks!!

David

---

### Post by valikor on 2009-06-19
Bump..

---

### Post by benerivo on 2009-06-19
I haven't had any experience of your situation, but if you are booting from the live cd and trying to access files from a mounted partition, then i would try...```
gksudo nautilus
```in a terminal window, which should overcome the permissions problems.

---

### Post by valikor on 2009-06-19
Thanks benerivo

I get this error when I enter "gksudo nautilus"

ubuntu@ubuntu:~$ gksudo nautilus

** (nautilus:5407): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


Thoughts?

---

### Post by louieb on 2009-06-19
Sounds like problems with the live CD.  Might want to run the check media for defects option. 

Does windows boot? A WUBI install is inside the windows file system. Does it have errors - did you run chkdisk in windows?

---

### Post by valikor on 2009-06-19
I checked the LiveCD and it detected no errors.

I ran "chkdsk C:/r" in Windows (I'm not sure if those are the right parameters--I'm somewhat ignorant on these issues.. but C:/ is where Wubi was installed)

It said the volume is clean. . . However, I do recall a few days ago when this problem was first arising, Windows prompted me at bootup and said that it strongly recommended I allow it to check the disk...

---

### Post by valikor on 2009-06-19
It might be worth noting that for some small percentage of my files (maybe 5%), I am able to access them/open them just fine. In some cases, two files of the exact same type (say, .txt) in the exact same directory may behave differently--one opens while the other gives me an error.

I assume this is pretty bad news--suggesting that something is badly corrupted?

---

### Post by benerivo on 2009-06-20
I might try a data recovery tool for corrupted files such as ddrescue. There is also a program called gddrecue, which i think is a graphical version, but i've never tried it. I would install ddrescue from the live cd, and try to recover important files to another disk or at least in to Windows on that disk.```
ddrescue '/vdisk/home/david/Desktop/untitled folder/100_2255.JPG' '/media/disk/recovery/100_2255.JPG'
```Where the first part of the ddrescue command is the possibly corrupted file, and the second part is a location on a usb disk that it will try to write the file to.

---

### Post by valikor on 2009-06-20
Problem solved

I actually just backed up my root.disk, then re-installed wubi and then replaced my root.disk with the original one. Now everything works fine.

I feel dumb for wasting so much time now, since this was such a quick fix. 

I still have no idea what was wrong though.

Thanks for all your help :)

David

---


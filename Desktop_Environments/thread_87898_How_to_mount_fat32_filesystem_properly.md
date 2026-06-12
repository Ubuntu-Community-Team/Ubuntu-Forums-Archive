---
title: "How to mount fat32 filesystem properly??"
date: 2005-11-09
forum: Desktop Environments
---

### Post by fei on 2005-11-09
I have a fat32 partition and want to share this partition between Ubuntu and windows. I have line of code in "/etc/fstab":
```

/dev/hda2       /mnt/wind     auto    rw,user,noauto,utf8     0       0

```

The problem is that all the files(including normal files and directories) are mounted with executable permission enabled, which is quite annoying. 

I need help to get this problem solved. Thanks in advance.

fei

---

### Post by Pablo_Escobar on 2005-11-09
Try :

/dev/hda2       /mnt/wind  vfat    iocharset=utf8,umask=000   0       0

:)

---

### Post by Buffalo Soldier on 2005-11-09
According to the [Official Start Guide](http://help.ubuntu.com/starterguide/C/faqguide-all.html), it's:
```
/dev/hda2 /media/wind vfat umask=000 0 0
```

According to the [Unofficial Ubuntuguide](http://ubuntuguide.org/), it's:
```
/dev/hda2 /media/wind vfat iocharset=utf8,umask=000 0 0
```

---

### Post by fei on 2005-11-09
I tried it that way. Still not working. 

What I found out is that if I use root account to mount the partition explicitly, it works find. If the partition is mounted automatically or by a normal user, then all files have executable permission enables. Don't know why???

---

### Post by Pablo_Escobar on 2005-11-09
Let me ask You then, what are You trying to accomplish ?
The way we've told is the proper way to mount FAT32 partitions.
You write You don't wan't all files to have executables flags ?? 
Please explain so I can understand what's Your goal.

---

### Post by fei on 2005-11-09
The problem is that all the files have the executable flags enabled, which is not what I want. I want only directories having the executables flags enabled, but not normal files.

Here is the list of part of the mounted partiion. Everything is marked executable, which is not what I want.
```

drwxrwxrwx  6 root root      8192 2005-10-20 03:57 linux-files/
-rwxrwxrwx  1 root root   2392205 2004-11-15 03:45 mj1.zip*
drwxrwxrwx  6 root root      8192 1980-01-01 00:00 my_CV/
-rwxrwxrwx  1 root root     19433 2005-08-05 21:16 my-cv.pdf*
-rwxrwxrwx  1 root root   1383853 2005-03-25 00:35 ProgrammingGroundUp-1-0-booksize.pdf*
-rwxrwxrwx  1 root root    380928 2005-02-23 19:09 putty.exe*
-rwxrwxrwx  1 root root    617113 2005-08-02 20:16 qt33-whitepaper-a4.pdf*


```


Thanks!!!

---

### Post by Pablo_Escobar on 2005-11-09
Wait, You want :
> drwxrwxrwx  6 root root      8192 2005-10-20 03:57 linux-files/
-rw-rw-rw-  1 root root   2392205 2004-11-15 03:45 mj1.zip* ??

---

### Post by fei on 2005-11-09
Yes. That's what I want. Only directories are marked executables. I know there is a option called "fmask" on mount. Just don't know how to use it

---

### Post by Pablo_Escobar on 2005-11-09
The general idea is like this :
if you want:
Human readable : rw-rw-rw-
Binary :              110110110
Octagonal :         6   6   6

Then the received octagonal numers You substract from the mask : 777
7-6=1
7-6=1
7-6=1

In that example it'd be **umask = 111**.

EDIT: try fmask = 111, dmask = 000

fmask - file mask
dmask - directory mask
Hope this little tutorial helps.

---

### Post by fei on 2005-11-09
It works now. I was confused by the explanation of "fmask" in the "man mount" page.

Here is the code
```

/dev/hda2	/media/wind	vfat	user,iocharset=utf8,fmask=111 0 0

```

Thanks for your help. You got my mind cleared. This had been annoying me for quite a while.


What I can't understand is that a usb flash drive, mounted automatically by the system, have all the permission flags marked properly. Don''t know how that works

---

### Post by fei on 2005-11-09
```

/dev/hda2	/media/wind	vfat	user,iocharset=utf8,fmask=111 0 0

```

After I use this line of code, I can never mark a file with executable flag.

---

### Post by Pablo_Escobar on 2005-11-09
Sorry, can't help You right now, I'm not on my U box to verify. Later on I'll chave a chance to verify it.

---

### Post by tOpEzz on 2005-11-22
wow nice... why ubuntu not automatically mount all the partition?? hejejje...or maybe one of you guy do some simple and easy to understand tutorial... for mount fat32 & ntfs partition.... hehehhe... because some new user like me is still noob with linux... ahaks..

---

### Post by aysiu on 2005-11-22
[QUOTE=tOpEzz]wow nice... why ubuntu not automatically mount all the partition??[/quote] I don't know why. Mepis and Knoppix do. > or maybe one of you guy do some simple and easy to understand tutorial... for mount fat32 & ntfs partition.... because some new user like me is still noob with linux... [http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

---


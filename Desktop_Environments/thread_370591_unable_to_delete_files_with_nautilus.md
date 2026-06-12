---
title: "unable to delete files with nautilus"
date: 2007-02-25
forum: Desktop Environments
---

### Post by Jimcanoa on 2007-02-25
Hello everyone,

I have just reinstalled Edgy Eft and it seems that Nautilus can't erase any file from a FAT32 partition I have in the same drive. It gives me the following error :
Error "Not on the same file system" while deleting "*path_of_file*"
This is my fstab file (I'm trying to delete files from /dev/hdb3/):
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb2
UUID=1c7a97e2-82a7-45c1-8efb-1ddb58ad7ef1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=08D052EED052E20C /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb3
UUID=45DC-6EA2  /media/hdb3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hde1
UUID=C2A412AEA412A547 /media/hde1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdf1
UUID=208C9CCA8C9C9BBA /media/hdf1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdg1
UUID=FCCCEB91CCEB450C /media/hdg1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=78488AF8488AB502 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=44387680387670B2 /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdc1
UUID=04506ED1506EC94E /media/sdc1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=443f811e-bd04-4eae-9777-e8467aadd824 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

/dev/hdb3 /mnt/data vfat umask=0000 0 0
```
Nevertheless, I can erase files with the terminal (so I guess the problem lies with nautilus).
I have erased ~/.nautilus and reinstalled nautilus (apt-get remove, restart and install again). And it didn't work...
Does anyone have any ideas?!

Thanks!

---

### Post by yabbadabbadont on 2007-02-25
Go into Nautilus' preferences and enable the option "Include a delete command that bypasses trash".  Then, when you go to delete something off the fat32 drive, right click on it and choose that option.  You may also be able to use shift-delete to bypass the trash like in windows, but I'm not sure.  By the way, I'm guessing that it is the trying to move the files to the trash that is causing your error.  I would have said permissions, but you said that it works from the command line.

Edit: Shift-delete does bypass the trash.

---

### Post by orb9220 on 2007-02-26
The problem for me anyways is to run a gksudo nautilus. Which allows me to copy and delete to any partition.

I have a nautilus icon on my panel that launches as > gksudo -g nautilus for the command. Works like a champ. the -g is the no grab screen flag so password dialog doesn't dim the screen on password prompt.

Beware tho when copying and editing files in root tho you can mess up system if you are not careful.

---

### Post by Jimcanoa on 2007-02-26
Thankyou guys, both options work beautifully. I wonder what's causing it, though, but for the moment I'll sitck with this.

Thanks again.

---

### Post by ardchoille42 on 2007-02-26
> **orb9220 said:**
> The problem for me anyways is to run a gksudo nautilus. Which allows me to copy and delete to any partition.

I have a nautilus icon on my panel that launches as  for the command. Works like a champ. the -g is the no grab screen flag so password dialog doesn't dim the screen on password prompt.

Beware tho when copying and editing files in root tho you can mess up system if you are not careful.

Are you certain you want to use the "-g" switch? That disables the "grab". This will make it possible for other X applications to listen to keyboard input events, thus making it not possible to shield from malicious applications which may be running.

---

### Post by orb9220 on 2007-02-27
Well my belief is if your system is that insecure already, then you have bigger problems than the -g option. 

> This will make it possible for other X applications to listen to keyboard input events,

And if they are already on your system to listen then they already have your password or am I mistaken? Always willing to learn.

I believe in security until it interfers with user productivity. In my case I work in the dark so the -g allows me to see the keyboard to type in password.  Wish I had a lighted keyboard.

---

### Post by ardchoille42 on 2007-02-27
> **orb9220 said:**
> Well my belief is if your system is that insecure already, then you have bigger problems than the -g option. 



And if they are already on your system to listen then they already have your password or am I mistaken? Always willing to learn.

Well, this is exactly what the grab is guarding against. If there's an app already on the system and listening, gksudo does what it does to prevent other apps from "getting" keyboard input. If you disable that (using -g), then that is circumventing gksudo's ability to protect against just that sort of thing.
Suppose I downloaded a file, or copied one off a cd, and ran it. Suppose that file had code that listens for keystrokes. If I disable gksudo's ability to prevent other apps from getting keystrokes, then I will be handing my admin password over to whatever that app will do with it. I'm not sure exactly what the ramifications are, but I don't feel comfortable disabling in-built security features and I like to inform others when I see them doing it.. especially if they may not realise they are disabling a security feature.

> **orb9220 said:**
> I believe in security until it interfers with user productivity. In my case I work in the dark so the -g allows me to see the keyboard to type in password.  Wish I had a lighted keyboard.

I would love a lighted keyboard :)

---

### Post by Norgz on 2007-06-08
In a quite similar case, I just had to add the .Trash-root and .Trash-`user' directories to /mnt/data. These directory had to be added, but they were not, it may be some kind of bug.

After adding them it worked perfectly.

---


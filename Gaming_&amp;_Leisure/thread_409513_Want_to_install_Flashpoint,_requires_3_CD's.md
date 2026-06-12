---
title: "Want to install Flashpoint, requires 3 CD's"
date: 2007-04-14
forum: Gaming &amp; Leisure
---

### Post by Dan_472 on 2007-04-14
Hello

I would like to try installing Operation Flashpoint (Game of the Year Edition).

The installation requires 3 CD's,   I place CD 1 in the drive   and 'wine' Setup.exe.  So far, so good.

A dialog box soon pops up asking me to insert CD 2.  However, the CD drive won't open, probably because wine or some other app is still using it.

Any suggestions?

I have two CD drives in my machine.   Also, I have plenty of Hard Drive space, so I  could  make a directory with all data from the 3 CDs.

Thank you

---

### Post by hikaricore on 2007-04-14
> **Dan_472 said:**
> Also, I have plenty of Hard Drive space, so I  could  make a directory with all data from the 3 CDs.

This is probably your best shot, copy all CDs to the same directory and run the install from there.

---

### Post by bugzor on 2007-04-14
force unmount cd

(in terminal)
```

sudo umount /mount/point/of/cd-drive -l
```

ie:
```

sudo umount /media/cdrom0 -l
```

after that you should be able to open tray and put next cd in.


i dont recommend that, but it should work.

---

### Post by Dan_472 on 2007-04-15
Still no go...  I have the contents of the CD's in a directory on the Hard Drive,  it still asks for CD 2, and I don't know how to tell "it" that the data's already there.

If I force the unmount of the CD drive (in /media/cdrecorder), I can now open the drawer, which is a plus, but when I put CD 2 in, nothing happens.

If I type

sudo mount /media/cdrecorder


I get  

mount: can't find /media/cdrecorder in /etc/fstab or /etc/mtab

I've also tried running Setup.exe from the Hard Drive, and having CD 2 already in the CD drive,  but it's like it won't "look" for it.  Unfortunately, the installation dialog box has only one button: Cancel.    I suppose it's supposed to auto-detect CD 2.

Any suggestions?

Thank you

---

### Post by Zeroedout on 2007-04-16
> **Dan_472 said:**
> Still no go...  I have the contents of the CD's in a directory on the Hard Drive,  it still asks for CD 2, and I don't know how to tell "it" that the data's already there.

If I force the unmount of the CD drive (in /media/cdrecorder), I can now open the drawer, which is a plus, but when I put CD 2 in, nothing happens.

If I type

sudo mount /media/cdrecorder


I get  

mount: can't find /media/cdrecorder in /etc/fstab or /etc/mtab

I've also tried running Setup.exe from the Hard Drive, and having CD 2 already in the CD drive,  but it's like it won't "look" for it.  Unfortunately, the installation dialog box has only one button: Cancel.    I suppose it's supposed to auto-detect CD 2.

Any suggestions?

Thank you

Um, your mount command is wrong. it should be sudo mount /dev/<WHATEVER YOUR CDROM IS CALLED>  Should the method still not work, (i'm pretty sure it does as I vaugly remember doing so myself) I would recommend using cedega to install and then wine to play. I know cedega has a method to not lock the cdrom drive.

---

### Post by deathbyswiftwind on 2007-04-16
I do believe he is right. Your cdrom should be called like cdrom0 in your fstab. Thats the way ubuntu has always set up my drives no matter what kind of cd drive i have

Just incase you dont know how to view your fstab

```

sudo gedit /etc/fstab

```

Im sure your device will be cdrom0 

While yours wont be the same as mine mine is listed as /dev/hdc /media/cdrom0
Mine is hdc because I have my hd split into two partitions and the cdrom is then appropriatly labeled the 3rd device.

---

### Post by Dan_472 on 2007-04-19
OK, the contents of /media/ are:
cdrecorder  cdrom  cdrom0

/media/cdrecorder  seems to be the directory where the setup files are.



If I type:
```
sudo gedit /etc/fstab
```

I get:


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
```


(the cdrom drive where the Flashpoint CD is, is likely the 4th drive,  /dev/hdd   I'm thinking)


If I type:
```
sudo mount /dev/hdd /media/cdrom0
```

I get:

```
mount: you must specify the filesystem type
```


What should I do next?

---

### Post by hikaricore on 2007-04-19
sudo mount /dev/hdd /media/cdrom0 **-t iso9660**

---

### Post by justin whitaker on 2007-04-19
If you get it running, let us know. :)

---

### Post by FaceLeg on 2007-04-24
My CD drive wouldn't let me change disks during an installation of Half Life 2 with Wine.  

After about 30 minutes of searching (and spamming variants of sudo eject at my console) I came across this thread.

Worked well, thanks!

---


---
title: "Other Drives?"
date: 2005-09-10
forum: Desktop Environments
---

### Post by srinath on 2005-09-10
How do I access the other drives like E:, etc? I came uptill filesystem in Places>Computer

---

### Post by cwaldbieser on 2005-09-10
[QUOTE=srinath]How do I access the other drives like E:, etc? I came uptill filesystem in Places>Computer[/QUOTE]
Generally speaking, the physical device should be represented by a logical device on your system.  You mount the logical device to a folder in your existing filesystem, and you can navigate to it from there.

I realize that sounds complicated, but an example should illustrate how simple it is.  Say you have two hard disks.  The primary one has a typical Ubuntu filesystem structure like /, /etc, /usr, /home.  Your second drive is full of photos, and is set up like:
```
/
/holidays2005
/holidays/2005/photo_001.jpg
...
/holidays2004
...
```
What you do is create a folder in your main system.  Let's say /photos.  Then you mount the second drive there.  Now, you can navigate to /photos/holidays/2005, etc.

Normally, this is either set up to be done automatically when you boot up for fixed storage like hard disks.  CD-ROMs and other removable media usually have an icon on your desktop you can click to mount/unmount them.  By default, they get mounted in a folder in the /media folder.

If you can explain a little bit more specifically what you want to do (always want the drive available? Is it removable? etc.), I'm sure someone can explain what you need to do to achieve your goals.

---

### Post by srinath on 2005-09-10
Ok! I have a dual boot. Two HDDs. One 20GB(10GB for Linux and 10GB for Windows) and one 40GB(four 10GB parts FAT32) I want to access the second HDD through Linux and windows. I want the second drive to be common to both.

And what you had to say earlier made a little sense. So, Thank you for the explanation.

---

### Post by Christoff UK on 2005-09-10
I think every person should read...

[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by cwaldbieser on 2005-09-10
[QUOTE=Christoff UK]I think every person should read...

[http://ubuntuguide.org/](http://ubuntuguide.org/)[/QUOTE]
Yeah, the section titled "Q: How to mount Windows partitions (FAT) on boot-up, and allow all users to read/write?" is what you want to look at.

---

### Post by srinath on 2005-09-10
Thank you.

---


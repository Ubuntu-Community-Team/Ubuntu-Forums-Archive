---
title: "Unable to change folder ownership..."
date: 2008-09-29
forum: Desktop Environments
---

### Post by hatman on 2008-09-29
I have a removable USB hard drive for backup purposes.  I usually copy my photographs over to it but this last time I've plugged it in Ubuntu wont let me as I dont have the necessary permissions.

I've tried to change the permissions using gksudo nautilus and that wont change them (current owner is root), so I resorted to command line and went down the sudo chown route, and that wont let me either...

> andy@downstairs:~$ sudo chown andy /media/sdd1/andy
chown: changing ownership of `/media/sdd1/andy': Operation not permitted


> andy@downstairs:~$ sudo chown andy /media/sdd1/andy/Pictures
chown: changing ownership of `/media/sdd1/andy/Pictures': Operation not permitted


All I want to do is drag and drop my photo folders from my main hdd to my backup USB hdd, it worked previously, any ideas? I'm lost...

EDIT: I've managed to drag/drop the photos usung gksudo nautilus, but would still like to change the ownership from root to me so I dont have to mess around...

---

### Post by Infinite Indefinite on 2008-09-29
Does your hard drive have some sort of physical write-protect?

---

### Post by ianhaycox on 2008-09-29
Running,

$ mount

from a terminal most probably shows the drive mounted read-only (ro)

This has happened to me with a USB Stick that was just pulled out without properly dismounting the drive. The normal sequence is if I insert the drive into a Windows box then forget to 'safely remove' the device, plugging it back into my Ubuntu box shows the same symptoms.

Try unmounting cleaning and/or using a Windows box to insert/remove safely.

---

### Post by hatman on 2008-10-03
> **ianhaycox said:**
> Running,

$ mount

from a terminal most probably shows the drive mounted read-only (ro)

This has happened to me with a USB Stick that was just pulled out without properly dismounting the drive. The normal sequence is if I insert the drive into a Windows box then forget to 'safely remove' the device, plugging it back into my Ubuntu box shows the same symptoms.

Try unmounting cleaning and/or using a Windows box to insert/remove safely.

Thats probably what it is, now I think on I seem to remember it being connected once and the PC hanging and I had to reboot...

I'll see if unmounting cleanly sorts it...

Thanks...

---

### Post by cool sam on 2008-10-03
HI
Congrats man for getting out of your problem.



_______________________________________________
 [IT Hardware](http://www.tig.com) | [IT Solutions](http://www.tig.com)

---


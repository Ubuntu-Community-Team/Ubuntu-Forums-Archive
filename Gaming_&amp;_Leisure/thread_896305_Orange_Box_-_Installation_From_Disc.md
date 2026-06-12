---
title: "Orange Box - Installation From Disc?"
date: 2008-08-21
forum: Gaming &amp; Leisure
---

### Post by Mashy on 2008-08-21
Ok, so I want to install the Orange Box (well, TF2 and Portal) onto Ubuntu. I can either wait ages for them to download from Steam, or I can install them from the dvd and wait less time for them to update.
Only problem is that I cannot insert the second disc. If I try to open it by pressing the button on the drive, it does not open (as always with Ubuntu, it would seem), and when I try to eject the disc from the Ubuntu desktop it says that it is in use and I should close any programs using it.

Is it possible for me to completely install the orange box from the dvds?

Oh, also, the orange box consists of two installation dvds which you have to insert one after the other. 

If not, it's not much of a problem, both TF2 and Portal are 50% installed, so at least it will have sped the time up.

Would installing it to my windows drive and then moving the files across work?

Thanks.

---

### Post by prshah on 2008-08-21
> **Mashy said:**
> 
Only problem is that I cannot insert the second disc. If I try to open it by pressing the button on the drive, it does not open

If you are installing it thru wine, then to eject you need to use the following command in a terminal (Applications-Accessories-Terminal)```
wine eject /dev/cdrom
``` Replace "/dev/cdrom" with your actual CDrom/DVDrom device. You can ignore the device specification if you have only one cd/dvd drive.

---

### Post by Mashy on 2008-08-21
> **prshah said:**
> If you are installing it thru wine, then to eject you need to use the following command in a terminal (Applications-Accessories-Terminal)```
wine eject /dev/cdrom
``` Replace "/dev/cdrom" with your actual CDrom/DVDrom device. You can ignore the device specification if you have only one cd/dvd drive.

Yes, I was installing through Wine. Thanks, that helps alot. XD

---

### Post by Catalyst2Death on 2008-08-21
the same command works with:
```
$ wine eject D:
```

---


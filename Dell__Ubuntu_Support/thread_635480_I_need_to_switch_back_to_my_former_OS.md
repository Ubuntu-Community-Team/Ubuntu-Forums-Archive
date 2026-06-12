---
title: "I need to switch back to my former OS"
date: 2007-12-08
forum: Dell  Ubuntu Support
---

### Post by Zero1010 on 2007-12-08
I need help switching back to vista even though it sucks I have all my favorite games there and I tried wine... too confusing. The only reason I downloaded ubuntu was the thought I could use it for web browsing and vista for gaming... but I tried just now and im like "OKAY... very funny where'd Vista go ubuntu STOP HIDING HIM NOOOOO!"

---

### Post by Shazaam on 2007-12-08
Open terminal (Applications>Accessories>Terminal) and type in...
```
sudo fdisk -l
```
(small L)
You will be asked for your password; type it in and hit enter. This code will print out your drive information in terminal. Copy and paste the output here.

---

### Post by Zero1010 on 2007-12-08
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30043   241320366   83  Linux
/dev/sda2           30044       30394     2819407+   5  Extended
/dev/sda5           30044       30394     2819376   82  Linux swap / Solaris

Is this good?

---

### Post by Zero1010 on 2007-12-08
hello?

---

### Post by markusf21 on 2007-12-08
looks like you wiped vista when you installed ubuntu

---

### Post by Zero1010 on 2007-12-08
OH **** what do i do now...

---

### Post by Shazaam on 2007-12-08
Yep, looks like Vista is gone. Try contacting Dell if it is a Dell pc and still under warranty for help.

---

### Post by Zero1010 on 2007-12-08
and they'll replace it? or send me vista disk?

---

### Post by mudguts on 2007-12-09
what kind of Dell do you have?  and when did you purchase it?  there should be some install disks shipped with it.  I have a dual-boot box with Vista and Ubuntu.. you may want to consider that when you re-partition your drive.   perhaps leave a 20GB partition or so for your swap file and install files..

good luck.

---


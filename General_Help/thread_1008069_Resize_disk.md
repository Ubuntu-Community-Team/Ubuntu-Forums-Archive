---
title: "Resize disk"
date: 2008-12-11
forum: General Help
---

### Post by Brian88 on 2008-12-11
Hi,
I have an installation of Ubuntu 8.04 (not 8.10) that was installed via Wubi on, err, around June 2008.
At that time, I placed the wubi folder on an 60GB partition in my 80GB drive, on Windows XP that 60GB partition is seen as D:\.
At that time, I assigned a 8GB size of Wubi virtual disk. 
Now, I have run out space of my /home folder, and I would like to expand it (because some apps need to use that folder ... and then now only 2GB left.)
How can I resize that disk to 16GB or something else? 
Thanks.

---

### Post by Yownanymous on 2008-12-11
Not sure how you would go about resizing the disk, but if you're willing to move it onto a permanent partition, try [LVPM]("http://lubi.sourceforge.net/lvpm.html").

---

### Post by Jammanuser on 2008-12-11
> **Yownanymous said:**
> Not sure how you would go about resizing the disk, but if you're willing to move it onto a permanent partition, try [LVPM]("http://lubi.sourceforge.net/lvpm.html").

uhh...u can resize it with LVPM as well! ;)

Cheers! ):P

-jammanuser

:guitar:

---

### Post by Brian88 on 2008-12-11
> **Jammanuser said:**
> uhh...u can resize it with LVPM as well! ;)

Cheers! ):P

-jammanuser

:guitar:

On the LVPM page it says :
Boot into windows and navigate to c:\wubi\disks, move the old virtual disk to a different folder as backup, and rename new.virtual.disk to home.virtual.disk

Oh no.
My Windows installation is broken now (so slow, painful, too many errors).
Can I move the virtual disk using another live CD (I have Ubuntu live-cds and Vista Live CD)?

---

### Post by Jammanuser on 2008-12-11
> **Brian88 said:**
> On the LVPM page it says :
Boot into windows and navigate to c:\wubi\disks, move the old virtual disk to a different folder as backup, and rename new.virtual.disk to home.virtual.disk

Oh no.
My Windows installation is broken now (so slow, painful, too many errors).
Can I move the virtual disk using another live CD (I have Ubuntu live-cds and Vista Live CD)?

Hold on...u want to MOVE the virtual disk? i thought u wanted to resize it! to move the virtual disk, i believe u can mount the Windows OS using a LiveCD, and then from there move it wherever u want! ;)

Cheers! ):P

-jammanuser

:guitar:

EDIT: haha...i had u confused there for a minute, didn't I? :D i understand that what u want to do is backup the virtual disk...and YES, u **can** copy the virtual disk to somewhere else from the LiveCD! simply mount the Windows OS using the directions that i give in my next post! Cheers! ):P

---

### Post by Jammanuser on 2008-12-12
To mount Windows using the Ubuntu LiveCD, run the following commands in a terminal: 

```
sudo mkdir /win
sudo mount /dev/sda3 /win

```
Note: replace "sda3" (if not correct) with with the correct device string, i.e. instead of "sda3", "sda2" or "sda1", etc. 

a=disk, and "3" equals the partition number...so if not correct, then just change it to the correct place where Windows is installed to! ;)

Let me know if it works or not...

Cheers! ):P

-jammanuser

:guitar:

---

### Post by clover7shoe on 2008-12-12
hey .. i cant seem to download pokerstars on this tbhing..i can..but i cant instyall??

---

### Post by Jammanuser on 2008-12-12
> **clover7shoe said:**
> hey .. i cant seem to download pokerstars on this tbhing..i can..but i cant instyall??

uhh...maybe u ought to post ur own thread about it, then, instead of talking it about it here! ;)

Cheers! ):P

Jam Man

:guitar:

P.S. check synaptic, and see if u can find it in the Quick Search box...and we can work from there! :lolflag:

---


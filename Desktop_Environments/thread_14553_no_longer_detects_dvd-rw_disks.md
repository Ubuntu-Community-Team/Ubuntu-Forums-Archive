---
title: "no longer detects dvd-rw disks"
date: 2005-02-08
forum: Desktop Environments
---

### Post by deuce868 on 2005-02-08
I just installed ubuntu 4 days ago and had it running. I had created some backups to dvd (created 4 disks) and today when I tried to do it the burner will not detect that the disk in the drive is a RW disk. I get the error from the gnome burner to:
Reload rewritable or blank media. Please replace the in-drive media by a rewritable or blank media. 

I have tried several disks. I bought a 10 disk pack so the 4 disks I did burn are of the same make/type as the ones I am using now. I can still pull up the disks I had burned previously and mount them fine. 

I cannot mount these blank disks, I get the error that no medium is found. 

Any ideas as to what's up? 

Thanks

---

### Post by scoon on 2005-02-14
Hey there, 

Try and load the disc and check dmesg for the err.


scoon

---

### Post by kamstrup on 2005-02-15
As far as I know you cannot "mount" a blank disk... - But Nautilus ought to pop up a cd-creator window when you insert one (unless you've disabled this feature)...

If I understand correct, you are trying to rewrite a CD-RW... Right? In doing so, you first have to blank it... If Nautilus is giving you problems with this, you might try pure 'cdrecord'... Go to a terminal and type 'man cdrecord' for instructions on how to use it.

---


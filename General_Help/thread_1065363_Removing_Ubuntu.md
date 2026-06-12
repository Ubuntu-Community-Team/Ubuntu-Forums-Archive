---
title: "Removing Ubuntu"
date: 2009-02-09
forum: General Help
---

### Post by draxz on 2009-02-09
Hello,

I have had ubuntu for almost 2 weeks now and I still not yet up and running.
There is soo much to work on, I need to download that and this and all the applications are in windows format (check my posts for all the problems I have faced and still not solved - my recent one wireless not shown)

Can any one tell me how Can I remove ubuntu, I currently have XP as my other OS

---

### Post by pikabuntu on 2009-02-09
You can use the live cd to delete the partition that contains ubuntu, but you will also have to fix the mbr.  this can be done with a windows install disk or a super grub disk.

---

### Post by draxz on 2009-02-09
so first I remove the partition and use the windows cd to install XP 

whats MBR

---

### Post by Dr Small on 2009-02-09
> **draxz said:**
> so first I remove the partition and use the windows cd to install XP 

whats MBR
Are you dualbooting and already have M$ XP installed?
MBR = Master Boot Record

---

### Post by theozzlives on 2009-02-09
MBR = Master Boot Record you just need to run fixmbr

---

### Post by pikabuntu on 2009-02-09
Do you already have xp installed?  
MBR = master boot record  which is pretty much replaced by grub when you install ubuntu

---

### Post by draxz on 2009-02-09
Yes I already have Xp installed

---

### Post by photon_man62 on 2009-02-09
OK then delete the Ubuntu partitions with GPartEd. (you can get it here: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php))

After that boot into the XP install CD.

Go to Advanced Options or whatever, and open up a command prompt. Type in fixmbr. And you're all set.

---

### Post by draxz on 2009-02-09
advanced you mean, in safe mode.

Cant I just use gpared and then boot into XP and type it in command prompt

---

### Post by markusf21 on 2009-02-09
you will need the xp cd to fix the mbr from the recovery console. you will not be able to boot xp until you do this

---

### Post by draxz on 2009-02-09
Can I remove the partition and install a fresh version of XP (will it remove Ubuntu and over write the MBR

---

### Post by photon_man62 on 2009-02-09
Yeah, you can format the partition and just install another OS over it.

And I DON'T mean safe mode.

---

### Post by draxz on 2009-02-10
well my Xp came with the boot cd which was provided by Toshiba.

When I book from cd, all it asks it to reinstall, delete partitions etc. Should I just go for the later part

---

### Post by photon_man62 on 2009-02-10
There's no option to boot into the Command Line? That's weird :?

---

### Post by draxz on 2009-02-10
No, when I boot its just showing me two options.

Delete partitions and reinstall or just reinstall OS.

Though it contains XP, its a toshiba boot cd.

---


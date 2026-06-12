---
title: "USB suddenly slow."
date: 2006-07-08
forum: Desktop Environments
---

### Post by someusernoob on 2006-07-08
I got a Creative Muvo mp3 player and usb 2.0

I suddenly get really slow speed, 5 mb in 3 minutes.

When i do
```

 sudo hdparm -t /dev/sda

```
i get: 
/dev/sda:
 Timing buffered disk reads:   20 MB in  3.27 seconds =   6.12 MB/sec


That seems normal, but it aint, it doesnt write this quick to the mp3 player when i copy files to it.

This is the line in my fstab for mounting it:
```

/dev/sda1	/media/MP3_Player	vfat	rw,user,noauto,sync,noatime	0	0

```

Anyone any suggestions? I allready turned my machine off and on, but the problem still exists. I worked fine from the 1st day i use Ubuntu, untill now.

Edit: forgot to mention that DMA is enabled on all my HDD's.

---

### Post by someusernoob on 2006-07-08
In the updates this morning was a file called:
pmount (0.9.11-1) to 0.9.11-1ubuntu1

It seems that this one has something to do with mounting removable devices as normal user.

So maybe im not the only one with this sudden problem? Can someone check out for me if your USB-stick/mp3player is slow suddenly?

---

### Post by someusernoob on 2006-07-08
After reading the description of that file (it should automount for users without a line in fstab), i removed my /dev/sda1 line from my /ect/fstab. Then I rebooted (just in case) and now i can write to my stick with full speed again. So it seems that there was some sort of a conflict between my fstab line and the pmount tool.

So the problem is solved for now i guess. And for everyone who got the same problem, backup your fstab line before you remove it!

---

### Post by bartbes on 2006-07-08
> **someusernoob said:**
> So the problem is solved for now i guess. And for everyone who got the same problem, backup your fstab line before you remove it!
As always with system files! I've had some problems with pmount in the past and that solved it too. BTW you can also comment out the line first, so you don't need a backup.

---

### Post by someusernoob on 2006-07-08
Thats possible too yes, didnt think about that. 

I'm a back-up fanatic, so i back up every important file that i change ...twice (one in the dir, one on another disk, if i reinstal i can copy my old configs back)... Just new to Linux and for the most things i know what i'm doing and what the change i make does, but sometimes its like Russian to me, so i feel more comfortable with backing up everything lol.

---


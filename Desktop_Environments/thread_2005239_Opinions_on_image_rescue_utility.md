---
title: "Opinions on image rescue utility???"
date: 2012-06-17
forum: Desktop Environments
---

### Post by Moozillaaa on 2012-06-17
I need one. The first one I read about is 'ddrescure', then I shut down for the evening. 

One partition is toast. The other 2 partitions on that drive, I can still mount.

Any other utilities that anybody is familiar with? The best perhaps???

And how about just the 'cp' copy command for an image? I've done this before when there were no problems, but the bad partition right now is giving me 'input/output' error, for some recovery task that I executed last night that I don't remember at the moment.

Backup, backup, backup.

I have 12.25 Terabytes of movies and music, ***ALL backed up***. But my /home (+ root)  partition wasn't backed up.

---

### Post by Moozillaaa on 2012-06-18
bumpin' here...

---

### Post by hwychld on 2012-06-18
With a healthy disk I use clonezilla, not sure about a failing disk though.

---

### Post by coldraven on 2012-06-18
Download Parted Magic
[http://partedmagic.com/doku.php](http://partedmagic.com/doku.php)

Boot with it and run Testdisc for partition repair or PhotoRec for image recovery.
Bear in mind that Testdisc could erase your two working partitions if you don't know what you are doing.
Best to dd the disc and work on the clone.
You will need to have a USB drive attached to store any data that is recovered.

---

### Post by Moozillaaa on 2012-06-19
> **coldraven said:**
> Download Parted Magic
[http://partedmagic.com/doku.php](http://partedmagic.com/doku.php)

Boot with it and run Testdisc for partition repair or PhotoRec for image recovery.
Bear in mind that Testdisc could erase your two working partitions if you don't know what you are doing.
Best to dd the disc and work on the clone.
You will need to have a USB drive attached to store any data that is recovered.

The dd clone is the first step I'm sure.

Would 'cp' copy task be better, to make a clone? Or perhaps 'dd'?

---


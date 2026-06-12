---
title: "I/O error while copying"
date: 2005-02-18
forum: Desktop Environments
---

### Post by Jad on 2005-02-18
Hi, Getting this error while trying to copy avi file from my CD. 
the CD is not currepted, I have test copying content on another box and it worked fine. 

```
Error "I/O error" while copying "/media/cdrom0/fightclub.avii".
```

Please advise.

---

### Post by dewey on 2005-02-18
Maybe there's a typo?
```

Error "I/O error" while copying "/media/cdrom0/fightclub.avi**i**"
```
Notice the extra "i" on the extension?

---

### Post by Jad on 2005-02-18
that how the file is called on the CD, I don't think incorrect file extention will give input output error.

---

### Post by dewey on 2005-02-18
Try another cd, can you extract data from it? (Using the same drive that gave you the error.)

---

### Post by Jad on 2005-02-18
Just copied about 3 another movies using same CD drive.

---

### Post by dewey on 2005-02-18
Rename the FightClub movie with a plain ".avi" extension, then try to copy it again, it's worth a shot.

ALso, can you play the movie directly from the cd?

---

### Post by Jad on 2005-02-18
I cant rename it its on CD
Yes I can play the movie directly from the CD.

---

### Post by dewey on 2005-02-18
Are you using a program to rip the file off the cd?  Or are you simply copying it, either by gui or terminal "cp *source dest*" ?

---

### Post by Jad on 2005-02-18
Well, I have tried both copy paste using GUI and command line. and got same error.

---

### Post by jdong on 2005-02-18
check output of "dmesg", especially towards the end.


Sounds like a damaged disk.

---

### Post by Jad on 2005-02-18
> Buffer I/O error on device hdc, logical block 176587
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
end_request: I/O error, dev hdc, sector 706352

 ](*,)

---

### Post by jdong on 2005-02-18
Yep, that's  damaged media!

You can try using a different CD-ROM drive to salvage your data, or use dd_rescue (google) to recover whatever you can  from the disk.

---

### Post by Jad on 2005-02-18
Thank you Jdong,

---

### Post by ecletrik on 2005-10-26
It's not damaged media!

I have the exact same problem except the disk will work/copy/whatever JUST DANDY on windows!

---

### Post by mahavishnu on 2006-08-27
same here.
I'm sure my CD isn't damaged.

Isn't it another Ubuntu bug??

---

### Post by nlz on 2007-12-04
I experience the same problem, but the weird thing is that windows has no problem copying the disk, although he's a bit damaged. Ubuntu seems to be quite sensitive on this point. Or am i talking nonsense now?

---

### Post by nlz on 2008-02-21
* bump *

a lot of people seem to have this problem (see google), but there seems no solution... anyone?

---


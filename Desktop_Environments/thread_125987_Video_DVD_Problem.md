---
title: "Video DVD Problem"
date: 2006-02-05
forum: Desktop Environments
---

### Post by Navyblue on 2006-02-05
I have a DVD ROM drive and a DVD writer drive. The last time I played video DVD was about more than a week ago and everything is fine. However right now I can't play any video DVD.

On the DVD ROM (hdc), when I insert a video DVD, the icon didn't even appear on desktop anymore, so not to mention playing it. Data DVD is detected and mounted fine.

On the DVD writer (hdd), the desktop icon appears when video DVD is inserted. However, that's the end of the good news.

The followings are the changes I have done to my PC lately.

- I meddled with hdparm so that my harddisk would turn off itself when not accessed. I wonder if it is related.

- I installed Windows and PowerDVD on this PC. I wonder if it does anything to the firmware if the optical drive and messed up my region code thingie. With the same disks that doesn't play in Linux, PowerDVD is able to play it from the DVD writer, but not from the DVD ROM.

- I installed two more 80 mm fans in my casing, each tapped power from each of the optical drives. I have since disconencted the fan and it doesn't help, I wonder if the drives can be permanently damaged from insufficient power. My power supply is 450 watts, I have 2 optical drives, 3 harddisks, ATI radeon 9550, Soundblaster Live! Value, an unused "winmodem", a video editting card, 1 CPU heatsink fan (120 mm), 2 circulation fan (50 mm I think), and the 2 exhaust fan (80 mm) which has been disconnected.

Thank you for reading.

---

### Post by nalmeth on 2006-02-05
You know more about this than I do, yet I must add anyway, have you made sure dvdcss is latest version? If data-DVD is working fine and not video-DVD, then this is all I can think of.

---

### Post by Navyblue on 2006-02-05
My libdvdcss2 is version 1.2.9-1 in the current Breezy repository.

---

### Post by Navyblue on 2006-02-05
:)

---

### Post by Navyblue on 2006-02-06
I've sort of narrowed it down to region problem. The symptoms are as follows

DVD ROM in Linux:
I am able to play some Asian video DVD that I believe was either region 3 or 6 (please tell me how to detemine it if you know). The earlier video DVD that I can't play I believe were from region 1. Region 1 (which I believe but not sure) video DVD were not detected at all.

DVD ROM in Windows:
Essentially the same thing with in Linux. I am able to play some Asian video DVD that I believe was either region 3 or 6. The earlier video DVD that I can't play I believe were from region 1. Region 1 video DVD were not detected at all.

DVD Writer in Linux:
Video DVD from all regions were detected, but I can't play anything. I believe it was due to some software configuration issue.

DVD Writer in Windows:
Video DVD from all regions were detected and played properly.

The weird thing is Windows listed both of my drive as region 1 and I am not able to play region 1 video DVDs.

I have downloaded a utilities that turns my DVD ROM into a region free drive. Now Windows detected it as a region free drive. But it still can't play region 1 DVD. On the other hand my DVD writer that is listed as region 1 is able to play anything that I put in.

So is it a firmware problem? hardware problem? Doesn't seems like a software problem now.

---


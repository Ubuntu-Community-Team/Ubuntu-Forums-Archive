---
title: "help me in fixing this"
date: 2006-08-19
forum: Desktop Environments
---

### Post by vilto on 2006-08-19
i just installed mplayer when i played a avi file in mplayer its playing but giving me this error.......what does it mean??

how do i fix it (im new to linux)

my graphics card is---- ati radeon xpress 2000 which is inbuilt in the motherboard

[[IMG]http://img245.imageshack.us/img245/2589/screenshotbv3.th.png[/IMG]](http://img245.imageshack.us/my.php?image=screenshotbv3.png)

---

### Post by kerry_s on 2006-08-19
right click on mplayer>preferences>video>select x11 by clicking on it than press ok and try again.

---

### Post by vilto on 2006-08-19
this alot ye it got fixed now:-D :-D :-D

---

### Post by noof on 2006-08-19
from [http://en.wikipedia.org/wiki/XVideo](http://en.wikipedia.org/wiki/XVideo) : 
> The X video extension, often abbreviated as XVideo or Xv, is a video output mechanism for the X Window System. Its main use today is to rescale video playback in hardware (namely in the hardware of the graphics card), in order to enlarge a given video or to watch it in full screen mode. Without XVideo, this scaling would have to be done in software, which is possible but requires a considerable amount of processing power, sometimes to the point of slowing down/degrading the video stream.

I was struggling with tearing when playing videos on my linux-box a few days ago. Turned out to be because I hadn't enabled xvideo. So if you get noticeable tearing and/or bad quality try to enable xvideo (depends on which graphics driver you're using)

---


---
title: "Screen refreshes really slow"
date: 2006-06-04
forum: Desktop Environments
---

### Post by zenlunatic on 2006-06-04
When I'm scrolling down a web page the screen refreshes in blocks (hard to explain).  What could possibly be causing this?

---

### Post by taurus on 2006-06-04
It's because you haven't installed a driver for your video card!!!  What kind of video card do you have?  For now, I assume it's nVidia so check out this link...

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by zenlunatic on 2006-06-04
Dell Inspiron 3500 features MagicMedia 256AV chip, also known as NM2200, that serves both as graphic and sound card.

---

### Post by Kjellvis on 2006-06-09
The NM2200 only accellerates in 16bit mode, while Ubuntu defaults to 24bit.  That means you have to edit your xorg.conf file and set the color depth from 24 to 16 bit for the resolution you are using.
To complicate matters, the NM2200 only accelerates video hardware overlay in 24bit mode.   So you have to choose, choopy desktop or choppy video.   I wish proper drivers would be released.  But this has been the same for my old Inspiron on any Linux/BSD installation I've tried.

Also I dont get any sound in Ubuntu, so I installed PC-BSD instead.

---


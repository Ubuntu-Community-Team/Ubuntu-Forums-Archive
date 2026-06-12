---
title: "Problems with firefox"
date: 2005-12-12
forum: Desktop Environments
---

### Post by d34th on 2005-12-12
Hi

I'm using firefox 1.0.7 on ubuntu breezy, but it doesn't start, it displays a segment violation error if I run it through a terminal

Here it is (in spanish)

toni@ubuntu:~$ mozilla-firefox
Violación de segmento
toni@ubuntu:~$

I think the only thing I've changed is the X config due to problems with acceleration, modelines... running dpkg-reconfigure xserver-xorg I don't think it is related but...

If it coud be useful, I can run Mozilla 1.7 perfectly

---

### Post by earobinson on 2005-12-12
could you translate "Violaci&#243;n de segmento" to english, im guessing it "segmentation error" but im not sure. If so I googled (firefox 1.0.7 linux segmentation error) and found this [http://www.linuxquestions.org/questions/showthread.php?p=1950324#post1950324](http://www.linuxquestions.org/questions/showthread.php?p=1950324#post1950324) Hope it helps

---

### Post by d34th on 2005-12-12
Thaks 
I'll have a look

I've noteced another thing.
If I run firefox as root, ir runs normally.
I think it coul be somithing about permissions, but I don't know what files and what permission must be right

---

### Post by earobinson on 2005-12-12
acording to the link above its a font problem. Let us know how it goes.

---


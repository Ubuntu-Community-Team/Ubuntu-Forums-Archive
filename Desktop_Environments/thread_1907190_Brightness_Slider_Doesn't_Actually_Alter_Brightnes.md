---
title: "Brightness Slider Doesn't Actually Alter Brightness"
date: 2012-01-10
forum: Desktop Environments
---

### Post by i0.sn0wl1nk on 2012-01-10
I'm using a HP Pavilion DV6TQE Laptop with Ubuntu 11.10 / Windows 7 dual-boot. Ever since I have installed Ubuntu, I have noticed that neither the brightness buttons on my laptop, nor the brightness slider in screen settings actually affect the brightness. The slider moves when I press the buttons, but the actual screen's brightness stays the same. As a note, it appears as though the actual brightness is stuck on approximately the maximum setting. Thanks in advance for any assistance.

---

### Post by i0.sn0wl1nk on 2012-01-13
(bump)

---

### Post by i0.sn0wl1nk on 2012-01-13
(bump)

---

### Post by KRISHNASHK on 2012-01-14
> **i0.sn0wl1nk said:**
> I'm using a HP Pavilion DV6TQE Laptop with Ubuntu 11.10 / Windows 7 dual-boot. Ever since I have installed Ubuntu, I have noticed that neither the brightness buttons on my laptop, nor the brightness slider in screen settings actually affect the brightness. The slider moves when I press the buttons, but the actual screen's brightness stays the same. As a note, it appears as though the actual brightness is stuck on approximately the maximum setting. Thanks in advance for any assistance.
hey where did u find the screen brightness adjustment slider in ubuntu 10.10? o any other ubuntu version!

---

### Post by i0.sn0wl1nk on 2012-01-25
System Settings > Screen Settings > Brightness.

---

### Post by i0.sn0wl1nk on 2012-05-08
Updated to 12.04 and the problem persists. Anybody have any ideas?

---

### Post by amalnath on 2012-07-23
I am also experiencing the same problem.
sometimes the brightness may become a bit less.
but after every restart or any further brightness adjustment, it returns to maximum.
any help appreciated.
:o

---

### Post by gordintoronto on 2012-07-23
Open a Terminal, and enter this command:
xgamma -gamma .5
You can try different values than .5, to see what works for you.

---

### Post by Toz on 2012-07-23
You could try point #3 from [here]("http://ubuntuforums.org/showthread.php?t=1964814").

---


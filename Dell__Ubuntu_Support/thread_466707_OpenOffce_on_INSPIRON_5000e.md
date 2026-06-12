---
title: "OpenOffce on INSPIRON 5000e"
date: 2007-06-07
forum: Dell  Ubuntu Support
---

### Post by simeli on 2007-06-07
xubuntu works fine on my dell inspiron 5000e, apart from being forced to change the display driver to vesa (i have a ATI Technologies, Inc. Rage Mobility M3 AGP 2x). 

when using openoffice tough, the window bar is scrambled. any ideas?

thank you.
s

---

### Post by tringabird on 2007-06-12
I just installed the "feisty fawn" Xubuntu on a Dell Inspiron 5000e and also had "video problems."  There were two or three vertical bands of pixel instability on the screen that garbled the display underneath.  I tried several different drivers, but finally went back to the "ati" driver, but reduced the default pixel depth from 24 to 16 in the Xorg config file, and that did the trick.

---

### Post by jstue on 2007-08-16
Hi there!

Just installed the "feisty fawn" Xubuntu on my good 'ole Dell Inspiron 5000e too... I've tried using both the "ati" and the "vesa" driver, but cant seem to get the "native" resolution on my screen? The highest resolution offered to me is 1024x768, but my machine is known to handle 1280x1024, and the "native" 1600x1200... 

...btw I'm also offered the lower resolutions 800x600 and 640x480...

What resolutions are you getting? :)

Jan-Erik

---

### Post by djairjr on 2007-10-25
I have the same problem with garbled pixels in 24bit Depth.

This not happen with 16bit.

Do you test the SVideo out with Gutsy? I`ve tested with Feisty, but is not working (garbled video).

I`ve found before that this issue is something with Mach64 subdriver of Ati default driver. Ati is not supporting this old cards. There is a security issue with 3d acceleration in this driver and this feature was removed due this. 

I can`t put the resolution higher than 1024x768. I still working on it.

---

### Post by Eric Lander on 2007-11-14
djairjr, any luck solving those issues?

I also have the 5000e, and cannot run above 1024 x 768, but would like to use the max resolution of 1400 x 1050.

---

### Post by greensweater on 2008-03-01
I also have the 5000e. Same problem with the garbled video. I used the xorg settings editor described above, used the VESA driver, added the 1400x1050 resolution and set to 16 bit color which solved the problem and I have full native resolution.

---

### Post by Evil Knievil on 2008-06-07
What kind of screen settings do you use? I think I have the 1400x1050 LCD display, but I don't know how to set this up correctly. Im hung at the 800x600 resolution.

---

### Post by ugm6hr on 2008-06-07
> **Evil Knievil said:**
> What kind of screen settings do you use? I think I have the 1400x1050 LCD display, but I don't know how to set this up correctly. Im hung at the 800x600 resolution.

I have now sold my 5000e, but it worked great with Fesity & Gutsy with the following: [http://ubuntuforums.org/showthread.php?p=3131272#post3131272](http://ubuntuforums.org/showthread.php?p=3131272#post3131272)

The VESA driver works initially, but then manually editing of xorg is necessary.

Not so sure with Hardy though.

---


---
title: "Regnum and the Intel 915 embedded graphics"
date: 2007-02-28
forum: Gaming &amp; Leisure
---

### Post by Ripfox on 2007-02-28
I just got a new laptop, have it all configured, wireless works sweet, beryl works sweet...but I cant get Regnum to launch with this machine, Some info: I do have 915resolution working. I can see glxgears. Regnum sees opengl. Launch=quick flicker, mouse pointer shoots up to top right corner. I can update it fine, just can't play. 

Any suggestions appreciated!

HPDV6000
1024 ddr2
Intel embedded graphics

---

### Post by sorcererx84 on 2007-02-28
Since Ubuntu's i810 driver (used by 915) is complete c**p, you probably can't play Regnum anyway. But if you still want to try, launch it from a terminal and post the output.

---

### Post by hikaricore on 2007-02-28
Aye, I can confirm that the i810 driver will NOT handle Regnum well/at all.  It was one of two games that hard froze my system when using this driver before I got my Nvidia card.  With the Nvidia card however it runs beautifully...  sadly with a laptop I know your options of video card replacement are null/limited.  :/

---

### Post by Ripfox on 2007-02-28
Are people working on this driver?

---

### Post by sorcererx84 on 2007-03-01
They are. Other distros' drivers are OK. In Mandriva 2007, I got over 1000 fps in glxgears.

---

### Post by Ripfox on 2007-03-01
how do you test fps

---

### Post by hikaricore on 2007-03-01
People have been discussing the drivers here and how they can be manually updated from packages from debian releases.

[http://ubuntuforums.org/showthread.php?t=364750](http://ubuntuforums.org/showthread.php?t=364750)

---


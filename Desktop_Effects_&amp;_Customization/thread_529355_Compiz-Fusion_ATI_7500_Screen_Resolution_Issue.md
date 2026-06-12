---
title: "Compiz-Fusion ATI 7500 Screen Resolution Issue"
date: 2007-08-19
forum: Desktop Effects &amp; Customization
---

### Post by spazzedout on 2007-08-19
I have 7.04, and I installed compiz-fusion without any issues. I have a laptop with a 7500 Radeon Mobility. 

The problem is when I enable the compiz effects, it cuts off more of my desktop, and there are some bugs such as windows not minimizing to window list.

Here is a screenshot of the issue I am having :

**[http://img477.imageshack.us/img477/8242/compizfusionatiwq1.png](http://img477.imageshack.us/img477/8242/compizfusionatiwq1.png)**

The effects seem generally smooth, but I need it to work at 1280x1024.

*Also note* that I am using a VGA connected monitor. The LCD on my laptop is dead. It's the main screen, not an extended desktop. However, I believe the issue may be due to 32mb vram, and it mirroring the screen to the external monitor and wasting memory. But that doesn't seem too likely ... then again, this laptop is OLD. 

Maybe there is some options I can adjust for fullscreen, or some minor resolution or frame buffer issue I overlooked. 

Suggestions?

---

### Post by overdrank on 2007-08-20
> **spazzedout said:**
> I have 7.04, and I installed compiz-fusion without any issues. I have a laptop with a 7500 Radeon Mobility. 

The problem is when I enable the compiz effects, it cuts off more of my desktop, and there are some bugs such as windows not minimizing to window list.

Here is a screenshot of the issue I am having :

**[http://img477.imageshack.us/img477/8242/compizfusionatiwq1.png](http://img477.imageshack.us/img477/8242/compizfusionatiwq1.png)**

The effects seem generally smooth, but I need it to work at 1280x1024.

*Also note* that I am using a VGA connected monitor. The LCD on my laptop is dead. It's the main screen, not an extended desktop. However, I believe the issue may be due to 32mb vram, and it mirroring the screen to the external monitor and wasting memory. But that doesn't seem too likely ... then again, this laptop is OLD. 

Maybe there is some options I can adjust for fullscreen, or some minor resolution or frame buffer issue I overlooked. 

Suggestions?

HI  This may not help but when I installed on a dell 640 with the ATI 7500 I had to lower the screen resolutions for that split screen to stop. Good luck! :)

---

### Post by chriscl on 2007-08-20
I've also had this on a laptop with a larger than 1024 x 768 screen (mine is 1400 x 1050).

The problem isn't the resolution, but the colour depth!

Edit your xorg.conf, and look for this section:

> 
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	16



I would guess that your "DefaultDepth" will be either 32 or 24? If it is, try reducing it to 16 (as above), then restart X and see what happens....

---


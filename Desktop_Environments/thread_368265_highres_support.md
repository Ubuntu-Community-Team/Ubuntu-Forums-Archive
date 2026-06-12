---
title: "highres support"
date: 2007-02-23
forum: Desktop Environments
---

### Post by hellospencer on 2007-02-23
Hi!

I'm trying to set up my Dell Ultrasharp TFT with Ubuntu. When selecting the supported resolution of 1600x1400 with xorg.conf, I run into problems, because the high resolution is only emulated (by extending the desktop over the monitor borders) and the actual resolution remains by somewhat like 1280x1024.

Thanks for suggestions and comments!

Cheers

---

### Post by lukescheminger on 2007-02-24
Hmm, I also had that problem trying to enable widescreen 1400x900 res. The way I got around it was manually changing one of the display settings in the xorg.conf file to the res that I wanted. I'm sure there must be a better way to fix this though, because I still can't figure out how to enable the full refresh rate my monitor supports. Maybe this will be of some help? If not, good luck.

---

### Post by Envirotech on 2007-02-24
How I got my refresh rate fixed was to look up my horizontal and vertical sync and then added that to my xorg.conf.  After I did that I got all my refresh rates fixed.  Here is a sample of my xorg.conf file.  Yours should be different.

Section "Monitor"
	Identifier   "GDM-400PS"
	HorizSync    30.0 - 94.0
	VertRefresh  48.0 - 160.0
	Option	    "DPMS"
EndSection

As to the original problem I do not know the answer.:(

---

### Post by tgalati4 on 2007-02-24
On a Dell Inspiron 7500 I got 1400 by 1050 to work by running
sudo dpkg-reconfiger xserver-org
control-alt-back              (to restart the xserver)

You might have to drop to 16 bit color depending on how much video RAM you have.  If you have shared video ram, check the BIOS for the amount.

Examine /var/log/xorg.0.log  to see how much video memory is being used by the selected mode.  It will also tell you how much is available.

Did you ask permission from your video card to install a high res monitor?

---


---
title: "Gnome shell graphics issues"
date: 2012-01-17
forum: Desktop Environments
---

### Post by tommyss4l on 2012-01-17
When I boot into gnome shell all the graphics are messed up and I suppose pixelated is the best term for it. The colors in the task bars are all wrong and scratchy, there are letters missing from the words in menus, it's insanity. 

I have tried uninstalling it and reinstalling it (through the Software Center) with the problem persisting. Any ideas on how to fix it?

---

### Post by hhh on 2012-01-17
You have to have a graphics card capable of 3D acceleration and the appropriate driver to run gnome-shell. Post your card and driver info and someone may be able to help you.

---

### Post by tommyss4l on 2012-01-18
Processor: Intel Core i7-870 Lynnfield 2.93GHz LGA 1156 95W Quad-Core Processor

Video Card: SAPPHIRE 100327L Radeon HD 6750 1GB 128-bit GDDR5 PCI Express 2.1 x16 HDCP Ready CrossFireX Support Video Card

---

### Post by lefuuuu on 2012-01-18
ati cards with the proprietary drivers in jockey don't work well with gnome shell. You can download the latest drivers from the ati website and build them if you don't want to use the open source ones. They work decently but still not perfect for whatever reason.

---

### Post by tommyss4l on 2012-01-18
Could you point me in the direction of someplace to teach me how to do that?

---

### Post by lefuuuu on 2012-01-18
[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

remove the proprietary drivers you're using now with:
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*

Then follow the "install catalyst manually" instructions.

Don't forget "sudo aticonfig --initial -f" after you install the created debs. 

I'd like to hear how the latest drivers are performing. The last ones I tried were 11.11 and they worked, but there were a few small graphical glitches here and there.

---

### Post by tommyss4l on 2012-01-19
Thanks, I'll let you know tomorrow

---

### Post by tommyss4l on 2012-01-20
Worked perfectly, thanks a lot!

---


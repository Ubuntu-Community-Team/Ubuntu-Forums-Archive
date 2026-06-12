---
title: "compiz disabled, cant get it up again..."
date: 2009-06-28
forum: Desktop Environments
---

### Post by nightshade209 on 2009-06-28
My compiz fusion effects have been disabled for some reason. They all show up as activated in CCSM, but none of them actually work. I set the Visual Effects option under Appearance to Extra, but it gets reset to None everytime i restart my PC. And even on Extra, only the minimize effect gets enabled. Pls help!

---

### Post by drs305 on 2009-06-28
Did you do an upgrade that may have disabled your hardware drivers? System > Administration > Hardware Drivers.

I found that in Jaunty, after several upgrades, instead of the few drivers that had been visible for a long time, I was presented with lots of drivers I'd never seen before. Additionally, the nvidia driver (180) that I had been using for months was no longer selected. I have had trouble reactivating it. I my case, recent attempts to activate it have failed. It starts to download, then fails.

So essentially I have the same problem as you do. The reason your effects are disabled is probably because the driver can't be enabled. Why we have lost that capability is now the question. I've tried different servers and even attempted to roll back to nvidia 173 without success.

**Update:** I reinstalled the nvidia-glx-180 via Synaptic and now I can restore the hardware driver and compiz.

---

### Post by nightshade209 on 2009-06-29
No, i did not perform any upgrades that affect the hardware. Besides, i do not use Nvidia. And the effects were working perfectly fine for like 1 n a half months even after upgrading to jaunty, so i doubt that is the problem.

---

### Post by VCSkier on 2009-06-29
What graphics chipset are you using, and when did this problem start?

---

### Post by VCSkier on 2009-06-29
There's a little script called "Compiz-Check" that can be really helpful in diagnosing problems like this.  It's really simple, but gives you all the information needed for troubleshooting.  Here's the link.

[Forlong's Blog - Compiz-Check]("http://forlong.blogage.de/entries/pages/Compiz-Check")

---

### Post by nightshade209 on 2009-06-30
> **VCSkier said:**
> What graphics chipset are you using, and when did this problem start?
I have an Intel inbuilt graphic card. Apart from that, i am afraid i do not know the details; though if you could tell me how to find them, i will post them soon. And, compiz has been acting up since 2-3 weeks. As far as i remember, i have done no major system updating or hardware changes during that time, though i may have installed/uninstalled a couple of programs.

---

### Post by nightshade209 on 2009-06-30
> **VCSkier said:**
> There's a little script called "Compiz-Check" that can be really helpful in diagnosing problems like this.  It's really simple, but gives you all the information needed for troubleshooting.  Here's the link.

[Forlong's Blog - Compiz-Check]("http://forlong.blogage.de/entries/pages/Compiz-Check")

I checked the link, and it passes my system. There are no problems flagged.

---

### Post by andrea000 on 2009-06-30
did you run compiz in the terminal maybe do that it might
point to a problem just open a terminal and type compiz

---

### Post by QIII on 2009-07-01
You can toggle between compiz and metacity by using the terminal --

compiz --replace

gets you to compiz.

metacity --replace

gets you to metacity.

Alternatively, you can add the Compiz Fusion Icon from Applications | Add/Remove, search for "compiz".  (See attachment.)

When you install Compiz Fusion Icon, you'll get a new icon on your panel.  If you double click it, you will get a new icon which you can right click and toggle between Compiz and Metacity using the "Select Window Manager" menu item.

---

### Post by nightshade209 on 2009-07-01
> **andrea000 said:**
> did you run compiz in the terminal maybe do that it might
point to a problem just open a terminal and type compiz

here is what i get:
```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1get fences failed: -1
param: 6, val: 0
Comparing resolution (1360x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: get fences failed: -1
param: 6, val: 0
present. 
Checking for Xgl: not present. 
get fences failed: -1
param: 6, val: 0
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

```

---

### Post by gjoellee on 2009-07-01
Might be a driver problem. Try xfix, and then install the graphics driver again. See how to do an xfix here: [http://www.kshoster.net/?q=tutorials-ubuntu-xfix](http://www.kshoster.net/?q=tutorials-ubuntu-xfix)

---


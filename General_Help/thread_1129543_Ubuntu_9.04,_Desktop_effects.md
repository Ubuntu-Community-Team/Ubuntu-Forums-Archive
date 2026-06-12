---
title: "Ubuntu 9.04, Desktop effects"
date: 2009-04-18
forum: General Help
---

### Post by niccholaspage on 2009-04-18
Well, whenever I want to enable Desktop effects, I get this error:
Desktop effects could not be enabled

On first boot and live CD, The effects worked fine. My laptop is a Toshiba A205-S5814. I don't have any display hardware drivers installed. Can anyone tell me why this is happening?

---

### Post by RedSingularity on 2009-04-18
You need the display drivers.  DO you know where to get the ones for your card?

---

### Post by niccholaspage on 2009-04-18
No, All I know is that the driver is an ATI one. Are you sure I need the display drivers? In the live CD and first boot, Effects worked fine.

---

### Post by niccholaspage on 2009-04-18
I tried doing lspci | grep VGA in BOTH live CD and install. (Live CD works with effects)
Both times, The command returned this!:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
```
Remember, Live CD works fine with effects, But my install doesn't.

---

### Post by RedSingularity on 2009-04-19
Thats interesting......all the Live CDs i have used never had effects.  So you have used an ATI driver for that intel card?  Looks like your driver is called "xserver-xorg-video-intel" in synaptic manager.

---

### Post by niccholaspage on 2009-04-19
I didn't install any graphic drivers, Just Ubuntu out of the box.

---

### Post by RedSingularity on 2009-04-19
Would you mind installing the graphics driver or would you rather not?  If you dont mind, try using the  "xserver-xorg-video-intel" in synaptic manager.  Then restart the Xserver with Ctl+Alt+Backspace.

---

### Post by niccholaspage on 2009-04-19
Ok, I will try and see how it goes.
EDIT: Terminal says its already installed.

---

### Post by niccholaspage on 2009-04-25
Bump, still don't have desktop effects.

---


---
title: "Newbie question - Activating desktop visual effects"
date: 2009-02-28
forum: General Help
---

### Post by Martynwills on 2009-02-28
Day one with Ubuntu and i&#7743; treading water a bit!

I&#7743; following Keir Thomas Ubuntu Pocket Guide and reference and I&#7743; trying to activate desktop visual effect.

I go SYSTEM- ADMINISTRATION - HARDWARE DRIVERS

The box that comes up says that I have a:

ATI/AMD proprietary  FGLRX graphics driver which is not activated. I cannot click on the button next to it and when I hit the activate button nothing happens.

I tried to approach the problem via SYSTEM - PREFERENCES - APPEARANCE -VISUAL EFFECTS which says that I have none selected. When I try to change to normal it says I ATI/AMD graphics driver activated. When I say activate it it tries then says DESKTOP EFFECTS COULD NOT BE ENABLED.

I&#7743; sure i&#7743; just being a newbie. Anyone able to point me in the right direction?

Cheers
Martyn

---

### Post by phr33k-dc on 2009-02-28
Try installing Compiz

---

### Post by Martynwills on 2009-02-28
I will do as it looks like it has loads of options but I haven got around to installing anything new yet. I would rather understand why its not working in this simple way first before i go and install more stuff if that makes sense?

---

### Post by aikiwolfie on 2009-02-28
ATI haven't had the best of luck with Linux lately. Basically their drivers are crap. Here's a link to the [ATI Linux Driver FAQ]("http://ati.amd.com/products/catalyst/linux.html"). Personally I don't think it's all that helpful.

The reason visual effects don't work is because Ubuntu is having trouble enabling the driver. Your graphics card might not be supported.

You can also open Synaptic via **System > Administration > Synaptic Package Manager** and do a search for **FGLRX**. Select the packages called **fglrx-amdcccle** and **xorg-driver-fglrx** for installation.

Alternatively open a terminal window use the following command.

```
sudo apt-get install fglrx-amdcccle xorg-driver-fglrx
```

I don't have an ATI card so I can't test this.

---


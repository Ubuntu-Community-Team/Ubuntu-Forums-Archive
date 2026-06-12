---
title: "No visual effects with Nvidia 169.07 drivers"
date: 2007-12-25
forum: Desktop Effects &amp; Customization
---

### Post by bluehue on 2007-12-25
Hello everyone,

I decided to update by drivers from 100.14.19 to 169.07 by taking the following steps:

1-Disabled restricted driver usage from Restricted Drivers Manager.
2-Removed the 100.14.19 drivers (nvidia-glx-new) via Synaptic Package Manager.
3-Stopped gdm and installed the latest nvidia drivers (NVIDIA-Linux-x86-169.07-pkg1.run) and also modified the "linux-restricted-modules-common" file to prevent the restricted modules from being loaded at boot (e.g. DISABLED_MODULES="nv").
4-Restarted gdm.

The drivers installed fine, but now I cannot use Visual Effects without having to revert back to the 100.14.19 drivers. For instance, selecting "Extra" from the Visual Effects tab asks me:
> 
Enable the Driver?

NVIDIA accelerated graphics driver (latest cards)

This driver is required to fully utilise the 3D potential of NVIDIA graphics cards, as well as provide 2D acceleration of newer cards.

If you wish to enable desktop effects, this driver is required.

If this driver is not enabled, you will not be able to enable desktop effects and will not be able to run software that requires 3D acceleration, such as some games.Enabling the driver prompts the system to download the previous 100.14.19 drivers I was running.

So my question is, how can I enable Visual Effects using the latest 169.07 drivers?:confused:

Thanks guys! :)

---

### Post by bigbrovar on 2007-12-27
am having exactly the same problem .... is there anybody that can help us

---

### Post by jomann on 2007-12-27
try searching in synaptic package manager, maybe that will help. search for something called compiz manager

---

### Post by Forlong on 2007-12-27
What's the output of ```
compiz
``` in a terminal?

---

### Post by bluehue on 2007-12-27
> **jomann said:**
> try searching in synaptic package manager, maybe that will help. search for something called compiz managerYeah, I forgot to mention that I had compizconfig-settings-manager already installed. It only gave me a new "Advanced Desktop Effects Settings" option in "Preferences", as well as the ability to customize my compiz configuration under "Visual Effects" under "Appearance Preferences".

---

### Post by bluehue on 2007-12-27
> **Forlong said:**
> What's the output of ```
compiz
``` in a terminal?This is what I'm getting:
```

spiral@spiral-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0040 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1600x1200) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
Window manager warning: Failed to load theme "Neutronium-Rounded": Failed to find a valid file for theme Neutronium-Rounded

/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Window manager warning: Failed to load theme "Neutronium-Rounded": Failed to find a valid file for theme Neutronium-Rounded
```
Edit: Forgot to mention that the "compiz" command re-enables visual effects, but are disabled as soon as I restart my machine and/or close the terminal

---

### Post by chewearn on 2007-12-27
This worked for my system:
Enable nvidia via the restricted manager.  Then, use envy to install new driver:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by bluehue on 2007-12-27
> **AstalaVista said:**
> This worked for my system:
Enable nvidia via the restricted manager.  Then, use envy to install new driver:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
Thanks. I'll keep this workaround in mind and will give it a try if no other solution comes up.

---

### Post by Forlong on 2007-12-27
> **bluehue said:**
>  the "compiz" command re-enables visual effects, but are disabled as soon as I restart my machine and/or close the terminal
Just add it to *System &#8594; Preferences &#8594; Sessions &#8594; Startup Programs* then.

---

### Post by bluehue on 2007-12-27
> **Forlong said:**
> Just add it to *System &#8594; Preferences &#8594; Sessions &#8594; Startup Programs* then.I can't believe I didn't think of this, given that I've done this many times before for several applications. Thanks man! Worked like a charm :guitar:

---


---
title: "Screen Resolution occationally changes after boot"
date: 2011-02-23
forum: Desktop Environments
---

### Post by TLangas on 2011-02-23
I find this extremely annoying.

The odd time I boot my laptop the screen resolution will change to 1024x768 and I would have to change it back to 1200x800. Not only that but I would have to move all the applets on the panel, to where they were.

This has been happening since I've first installed Ubuntu 7.10 and continues to 10.04. I've yet to see a fix on the Ubuntu Forums.

Here's some information about my screen.
[B]sudo lshw -C video:
[/B]```
  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:29 memory:d0000000-d03fffff memory:c0000000-cfffffff(prefetchable) ioport:5140(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:d3500000-d35fffff
```On the odd occasion I do add a second monitor (projector) for presentations. I thought that was the cause, but the screen change does not occur in a predictable manor.

Any suggestions besides "ewww Intel"?

---

### Post by Krytarik on 2011-02-23
You can try to set the resolution(s) with "xrandr" on boot:
[https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions")

---

### Post by TLangas on 2011-02-24
I don't think that will help much as the starting resolution when the desktop loads will still cause the panel items to be rearranged.
Thanks for your input.

---

### Post by Krytarik on 2011-02-24
> **TLangas said:**
> I don't think that will help much as the starting resolution when the desktop loads will still cause the panel items to be rearranged.
Thanks for your input.
If you set up xrandr to run in the "permanent" way described in the guide, it will be run when the login screen (GDM) loads.

---

### Post by TLangas on 2011-02-24
Okay I set up a .xprofile. Let's see if it happens again.

---

### Post by Krytarik on 2011-02-24
> **TLangas said:**
> Okay I set up a .xprofile. Let's see if it happens again.
Oh, you should set it up in the kdm/gdm startup scripts. The way you set it up is user specific and xrandr is indeed called AFTER you log in. I should have mentioned it before, but this is also explained in the guide.

---

### Post by TLangas on 2011-02-24
Apparently setting **xrandr -LVDS1 -auto** on the login screen causes the resolution to go to 1024x768, but doing the same from the desktop changes it to the correct 1280x800.

I was able to force it with **xrandr -LVDS1 -mode 1280x800** in the **/etc/gdm/Init/Default** file. Thank you.

---


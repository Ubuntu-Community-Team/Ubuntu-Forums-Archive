---
title: "How to know which driver to install?"
date: 2009-05-28
forum: General Help
---

### Post by havencruise on 2009-05-28
This question just popped up while discussing about Ubuntu with my colleagues. How should one know what graphics driver is appropriate to install in systems?Shouldn't there be a driver that's meant only for a system of a particular configuration??

I'm running Intrepid on Toshiba Satellite L300 and I still seem to be confused about which driver to install to make the Compiz effects work. :P
Here's my hardware profile.
Intel Dual Core T3200; 3GB DDR2 Ram; And I do not know how to check which graphics card I have, or whether I have one or not. 
I would like to know that and which driver to install.

---

### Post by spiceminesofkessel on 2009-05-28
Type this command:
```
lspci
```

This will give you a profile of your hardware and may help you determine which video card you have. You may also check the Toshiba website and locate your system's build and see which video card came with your system.

---

### Post by ptn107 on 2009-05-28
Depends on which of the L300 models you have, each have different graphics hardware:

L305-S5921 - Intel® Graphics Media Accelerator 4500M

L305D-S5928 - ATI Radeon™ 3100 Graphics Card

L300-ST3502 - Intel® Graphics Media Accelerator 4500MHD

There's a sticker on the bottom of your laptop that will have one of those numbers.

---

### Post by havencruise on 2009-05-28
> **ptn107 said:**
> Depends on which of the L300 models you have, each have different graphics hardware:

L305-S5921 - Intel® Graphics Media Accelerator 4500M

L305D-S5928 - ATI Radeon™ 3100 Graphics Card

L300-ST3502 - Intel® Graphics Media Accelerator 4500MHD

There's a sticker on the bottom of your laptop that will have one of those numbers.

Thanks a lot for this. I found a sticker something similar to the 3rd one. It reads : [I]
Satellite L300 System Unit.
T320 1024 GL40 250 15WC DMD g 6C NOS 1Y[/I]
Could you explain as to what they stand for?

Also I followed the "lspci" command and found two lines on my graphics card:
[I]00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
[/I]
Which one am I supposed to install?

---

### Post by Legace on 2009-05-28
> **havencruise said:**
> Which one am I supposed to install?

You've got to install the Intel graphics driver.
I believe the driver is called **xserver-xorg-video-intel**

---


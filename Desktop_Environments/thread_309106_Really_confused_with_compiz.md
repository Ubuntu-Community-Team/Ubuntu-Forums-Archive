---
title: "Really confused with compiz"
date: 2006-11-29
forum: Desktop Environments
---

### Post by paparucino on 2006-11-29
Hi guys,
I'm reading tons of post about installing and running compiz. I'ld like to try it, but it seems to be a nightmare. :-)
My video card is a Radeon 9200 SE and I've already installed compiz, -core, -gnome, -plugins.
My big trouble is: can compiz run with tha video card?
What is the correct procedure?
Thank you in advance.

---

### Post by pay on 2006-11-29
Open your xorg.conf ```
gksudo gedit /etc/X11/xorg.conf
```
and change the line ```
Section "Device"
        Driver      "fglrx" # (or vesa or some other driver)
EndSection
```to```
Section "Device"
        Driver      "radeon"
EndSection
```

and also add this to the end of your /etc/X11/xorg.conf

```
Section "DRI"
        Group 0
        Mode 0666
EndSection

Section "ServerLayout"
        Option         "AIGLX" "true"
EndSection

Section "Extensions"
        Option         "Composite"   "Enable"
EndSection

Section "Device"
        Option      "XAANoOffscreenPixmaps" "true"
        Option      "DRI"     "true"
EndSection

Section "Screen"
        Option      "DefaultDepth"     24
EndSection
```Then install beryl```
sudo aptitude install beryl-manager emerald-themes
```Now add "beryl-manager" to Desktop --> Preferences --> Sessions --> Startup Programs

---

### Post by pay on 2006-11-29
Cards Supported

    * ATI: Radeon 7000 through X800 (r100, r200 and r300 generations)(9250-X800 supported by the experimental r300_dri driver)
    * Intel: i810 through i945
    * nVidia: all cards, except those covered by the legacy driver. 9xxx driver series only. (See HOWTO nVidia GL Desktop Effects.) 

[edit]
Cards In Testing

    * ATI: Radeon 9500 through X850 (r300 and r400 generations), at least with the opensource drivers.
    * ATI R200-seem to work but very slow
    * Intel 845G-Compiz Segfaults
    * Intel 855GM-Had trouble getting compiz, and old compiz-quinnstorm to work but beryl works flawlessly.
    * Intel 865G-Works very nicely with Xorg 7.1 and compiz ebuild in official tree
    * Intel GMA900/i915: Works pretty well without blurring effects and is pretty stable. Used opensource-drivers x11-drivers/xf86-video-i810-1.7.0-r1. Can start and stop beryl at will.
    * Savage: works but some slowdown with DRI drivers shipping with X.org 7.1. Savage are certainly not so performant cards.. but works :) It is not possible at the moment, however, to start compiz/beryl or composite metacity. 

[edit]
Cards Not Supported

    * ATI: Rage 128. Looks like driver locking issue.
    * ATI: Mach64. No DRM support in Fedora, still insecure.
    * Matrox: MGA G200 to G550. Needs at least a driver update to fix DRI locking. PCI cards probably have other issues as well.
    * 3dfx: Voodoo 1 and 2. No DRI driver.
    * ATI: Radeon 8500 through X850 with the closed fglrx driver. Uses an ancient version of the DRI driver API that can't work with the new driver loader. No ETA on closed driver support.
    * ATI Radeon Xpress 200M (memory init or something)
    * Anything without a free 3d driver.
    * nVidia: older cards covered only by the legacy driver. 

[edit]
Unknown Status

    * Via
    * Sis 

From [http://gentoo-wiki.com/HOWTO_AIGLX](http://gentoo-wiki.com/HOWTO_AIGLX)

---

### Post by paparucino on 2006-11-29
> **pay said:**
> Cards Supported

    * ATI: Radeon 7000 through X800 (r100, r200 and r300 generations)(9250-X800 supported by the experimental r300_dri driver)

Which means, if I'm not wrong, that I cannot use compiz-beryl.
I'm I right?

---

### Post by mcduck on 2006-11-29
There's always option to use XGL instead of AIGLX, so you should also check if that supports your graphics card..

---

### Post by pay on 2006-11-29
I think that it means all the ones between ATI: Radeon 7000 through X800

---


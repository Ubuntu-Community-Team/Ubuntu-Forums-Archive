---
title: "Background walllpaper + desktop icons disappear when compiz runs"
date: 2007-11-02
forum: Desktop Effects &amp; Customization
---

### Post by twelve17 on 2007-11-02
Googling around, I haven't been able to find someone else having my precise problem.

I'm on Gutsy, using a Nvidia GeForce 8400 video card.  I have a dual head setup and am using the TwinView feature to expand my X onto my two displays (one being 1680x1050 and the other 1280x1024).

When I run compiz, my desktop wallpaper and icons disappear.  The desktop background turns black.  The rest of the visual effects seem to work fine.  If I switch the effects off, I see the original desktop wallpaper and icons again.


Here is my driver version:

---------------------------------------

Package: nvidia-glx-new
Source: linux-restricted-modules-2.6.22 (2.6.22.4-14.9)
Version: 100.14.19+2.6.22.4-14.9

---------------------------------------


Here is the output of my .xsession-errors when I enable visual effects:

---------------------------------------

nvidia_new restricted driver is already enabled
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0422 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2960x1050) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

---------------------------------------


Here are the relevant portions of my xorg.conf:

---------------------------------------

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "MetaModes" "CRT: 1280x1024 +1680+0, DFP: 1680x1050 +0+0; CRT: 1280x1024 +0+0, DFP: NULL"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---------------------------------------

Here's partial output of my Xorg.log:

---------------------------------------

(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "MetaModes" "CRT: 1280x1024 +1680+0, DFP: 1680x1050 +0+0;
 CRT: 1280x1024 +0+0, DFP: NULL"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 8400 GS (G86) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 60.86.4a.00.25
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 8400 GS at PCI:1:0:0:
(--) NVIDIA(0):     Philips 170B2 (CRT-1)
(--) NVIDIA(0):     DELL E207WFP (DFP-0)
(--) NVIDIA(0): Philips 170B2 (CRT-1): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): DELL E207WFP (DFP-0): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): DELL E207WFP (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Display Devices found referenced in MetaMode: CRT-1, DFP-0
(II) NVIDIA(0): Assigned Display Devices: CRT-1, DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "CRT:1280x1024+1680+0,DFP:1680x1050+0+0"
(II) NVIDIA(0):     "CRT:1280x1024+0+0,DFP:NULL"
(II) NVIDIA(0): Virtual screen size determined to be 2960 x 1050
(--) NVIDIA(0): DPI set to (95, 96); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp

---------------------------------------


I am NOT using the Xinerama extension.

I tried installing xgl, and compiz works correctly, showing the background.  However, the way that the dual-head desktop behaves under XGL is a little different vs. when xgl is not installed*.  I prefer the non-xgl behavior.

Any help would be appreciated!

Thanks,

Alex

* Under XGL, when you maximize windows, they maximize across both screens.  Also, you can't seem to just have a panel on one of the screens.  Under regular X, the desktop still spans across the two screens (i.e. you can drag windows between them), but Gnome is somehow still aware of the two sides.

---

### Post by Stemp on 2007-11-02
What happen when you restart Nautilus in a terminal ? 

NB : to get the important parts of your xorg log try theses lines :
```
cat /var/log/Xorg.0.log | grep EE
cat /var/log/Xorg.0.log | grep WW

```
The first one is to get the Errors (I guess you have none) and the second the Warnings

---

### Post by twelve17 on 2007-11-02
Hi Stemp.  Thanks for your reply.

When I run nautilus from the terminal, the "home folder" window pops up.  The desktop and icons are still gone.  No errors are printed on the terminal.

I am under the belief that when I turn on compiz, nautilus is still running, but compiz is simply covering the desktop "layer" with the black background.

Here's the output of the EE/WW greps:

```

alex@xyz:~$ cat /var/log/Xorg.0.log | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) Failed to load module "type1" (module does not exist, 0)

alex@xyz:~$ cat /var/log/Xorg.0.log | grep WW
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) Warning, couldn't open module type1

```


Alex

---

### Post by twelve17 on 2007-11-02
On a side note, the first two lines of each grep is actually Xorg enumerating what the various codes mean:

```

alex@xyz:~$ grep -B5 WW /var/log/Xorg.0.log 
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.

```

---

### Post by twelve17 on 2007-11-02
Here's an interesting bit I discovered:

1. Turn off desktop effects (background wallpaper and icons appear)
2. Open gnome-terminal.  (I have the transparency set so I can see the BG)
3. Turn on desktop effects.

Once I do #3, the background disappears, except for behind the terminal! I can move the terminal around and the background changes as if it were there.  It's kind of hard to explain, so I attached a screenshot in hopes it helps. The terminal on the left side is showing the background.

Alex

---

### Post by Stemp on 2007-11-02
:confused: Strange behavior.

Do you have a wallpaper set in compiz ? Do you have compizconfig-settings-manager installed ?

---

### Post by twelve17 on 2007-11-02
> **Stemp said:**
> :confused: Strange behavior.

Do you have a wallpaper set in compiz ? Do you have compizconfig-settings-manager installed ?

I don't recall setting a wallpaper in compiz.  Where can I verify this?  (I do see that the compiz.real binary takes a --bg-image parameter, but that is not being set).

I do not have  compizconfig-settings-manager installed.

Strange behavior indeed. :)

---

### Post by twelve17 on 2007-11-02
Sorry, my mistake.  I DO have compizconfig-settings-manager installed.

---

### Post by Stemp on 2007-11-02
So check in the cube settings, there is something about a background. But I'm not even sure, and I don't know why it will overwrite the nautilus background :(

---

### Post by twelve17 on 2007-11-05
I believe there are some kind of image settings for the desktop cube background.  However, I tested under a brand new user.  Feisty's default desktop effects use the "desktop plane" instead of the cube.  The problem still persisted. :(

Thanks for your help anyway. :)

---

### Post by twelve17 on 2007-11-05
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/160226](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/160226) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I've filed a bug for this.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/160226](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/160226)

---


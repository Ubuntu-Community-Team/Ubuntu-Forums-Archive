---
title: "Using nvidia X Server disables desktop effects in Kubuntu"
date: 2011-09-22
forum: Desktop Environments
---

### Post by n8af on 2011-09-22
Hey guys,

I'm using the KDE GUI with ubuntu and after setting up the enviroment i noticed the desktop effects options was "temporarily disabled".  When I try to enable it, the notification bar pops up a message saying: "Desktop Effects have been suspended by another application."  

Now i've had a go-around with the nvidia drivers in order to get my dual monitor setup working like I want.  Before, (when only one monitor was working) I was able to play with the desktop effects and they worked just fine.  Then, once I got both monitors working by using X Server and enabling Xinerama, I noticed that ever since I enabled the nvidia X Server, the desktop effects went away.

**Is there a way to override the x server settings to allow desktop effects?**  

I'm using two Nvidia GeForce 285 GTX in SLI - so its not a question of hardware capability.

Kubuntu looks beautiful spread across the two monitors, i just wish I could go that extra step and enable the box workspace switching, etc.

Thanks in advance for any advice.

---

### Post by n8af on 2011-09-22
I ran across this article [here]("http://pebblesinthesand.wordpress.com/category/kubuntu/")

At the very end, the author explains that he wasn't able to get the desktop effects working with nvidia drivers either. 

Is there a known issue with nvidia graphic drivers and using desktop effects?

---

### Post by sumski on 2011-09-23
What Kubuntu version are you using?
[http://cgit.freedesktop.org/xorg/xserver/commit/?id=84a14fab8f930ef1855444ae4e9e3e14ee008328](http://cgit.freedesktop.org/xorg/xserver/commit/?id=84a14fab8f930ef1855444ae4e9e3e14ee008328)

There shouldn't be conflicts between compositing and xinerama with xorg-server >= 1.10

---

### Post by sumski on 2011-09-23
Also, take a look at this:
[https://wiki.archlinux.org/index.php/Xorg#NVIDIA](https://wiki.archlinux.org/index.php/Xorg#NVIDIA)

---

### Post by n8af on 2011-09-23
> **sumski said:**
> What Kubuntu version are you using?
[http://cgit.freedesktop.org/xorg/xserver/commit/?id=84a14fab8f930ef1855444ae4e9e3e14ee008328](http://cgit.freedesktop.org/xorg/xserver/commit/?id=84a14fab8f930ef1855444ae4e9e3e14ee008328)

There shouldn't be conflicts between compositing and xinerama with xorg-server >= 1.10

I'm using natty

---

### Post by n8af on 2011-09-23
> **sumski said:**
> Also, take a look at this:
[https://wiki.archlinux.org/index.php/Xorg#NVIDIA](https://wiki.archlinux.org/index.php/Xorg#NVIDIA)

So based on this article, nvidia does disable desktop effects when using Xinerama.  

I changed the options to enable twinview.  Now i have desktop effects working, however, i can't drag a window from my source monitor to the right monitor and vise versa.  

So is this one of those turning points where I have to decide which I would rather have?  Desktop effects, or a wide spannable desktop?

Why does Nvidia disable the effects with Xinerama?

---

### Post by sumski on 2011-09-23
I don't have Nvidia, so can't help you further :(

[http://us.download.nvidia.com/XFree86/Linux-x86_64/256.53/README/index.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/256.53/README/index.html)

---

### Post by n8af on 2011-09-23
After reading through the documentation you provided and tinkering around with some of the settings. I was finally able to get it to work!!!!!!!!!  \\:D/
:guitar:

Finally!  I'm not exactly sure which configuration change took the cake, but for those who may experience the same issue, below is the brunt of my xorg.conf file.
Note: I am running two nvidia gpu's in SLI - comment out or remove SLI settings if you are not using SLI.

```
Section "ServerLayout"

    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "TwinView" "1"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer X223W"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Acer X223W"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 285"
    BusID          "PCI:3:0:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 285"
    BusID          "PCI:3:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "MultiGPU" "on"
    Option         "SLI" "on"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "DFP-0: nvidia-auto-select +1680+0, DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
    Option         "MultiGPU" "on"
    Option         "SLI" "on"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---


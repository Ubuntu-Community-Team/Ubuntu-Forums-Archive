---
title: "Twinview problems after 10.04 upgrades"
date: 2010-04-30
forum: Desktop Environments
---

### Post by Loyd Gravitt on 2010-04-30
I upgraded from 9.04 to 9.10 yesterday afternoon and then from 9.10 to 10.04 this morning.  The only issue I have had is with my dual monitor twinview setup.  I saw the one thread (solved) about the downloading the latest nvidia driver, which I did.  This allowed me to have a single wide image strecthed across both monitors as my background instead of two separate copies of the same image.

But now, when I maximize a window, it two fills both monitors instead of snapping to a single display like it did on 9.04, and the pictures folder screensaver now displays only a single image centered across both monitors instead of a different image on each display.

I have restored my old xorg.conf, but that didn't fix the problem.  Any ideas?

---

### Post by Loyd Gravitt on 2010-05-03
Bump

---

### Post by Loyd Gravitt on 2010-05-04
Bump

---

### Post by phsamuel on 2010-05-04
Exactly the same problem. But I have the problem for 9.10. I was thinking to upgrade to 10.04 to see if the problem will be solved. I guess I don't need to try...

---

### Post by pietermeurs on 2010-05-28
I have the same problem as well. However, I just did a clean install of 10.04 (on my laptop) and did not yet enable the Nvidia driver. I did however try to connect my second monitor (through system - preferences - monitor). This resulted in the right solution: maximizing only happened in one monitor. 

However, after installing the nvidia driver, I lost this again, just able to click twinview in the nvidia-settings resulting in a maximization over the two screens. 

Maybe this helps someone to understand the problem better?

---

### Post by pietermeurs on 2010-05-28
I had another look at the drivers (system - administration) and saw i didn't select the most recent nvidia driver. When I did this, the problem was gone: maximizing only happens in one screen

---

### Post by novafire on 2010-06-03
I have a similar issue with the current version of the nvidia drivers as of today.  This issue also stretches the top and bottom Gnome panels across both screens which is not something I want either.

---

### Post by carsonrose on 2010-06-03
I used to have this problem........... go to hardware drivers... then choose the recommended driver..... then open xorg.conf......(/etc/X11/xorg.conf) make it look like this:


Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
        Option  "Twinview" "TRUE"
EndSection


[SIZE=4]Notice under DEVICE there is an option "Twinview" "TRUE"

then save and reboot........ problem solved[/SIZE]

:guitar:

---

### Post by novafire on 2010-06-03
Hmmm, I added the option to make mine look like this:

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:1:0:0"
    Option         "Twinview" "TRUE"
EndSection

and rebooted, but it did not help.

---

### Post by purecharger on 2010-06-22
Same exact problem. How to get it to only maximize to one screen?

---


---
title: "Black window when running VMWare-server"
date: 2007-08-13
forum: Desktop Effects &amp; Customization
---

### Post by VictorR on 2007-08-13
I have noticed that when I am running VMWare-server (Windows 2000 as a guest system) on Ubuntu Feisty some windows open black in their client area.
More details:
Computer - AMD Athlon-XP 2600+, 1 GB RAM, NVidia GeForce4 MX440 video card.
Host system - Ubuntu Feisty Fawn, NVidia driver from Ubuntu repository (as I remember) installed with no problems, Gnome + Compiz Fusion + Emerald.
Everything works fine until I launch VMWare-server with Windows 2000 as a guest system. I don't see any troubles inside virtual Windows, but If I open some extra windows in Ubuntu they sometimes (!) are black - window decorations (by Emerald) are fine, but the client area is just black.
The affected window can be from any program - Text Editor, Nautilus, Swiftfox. It does not happen always - one can try to close the program and launch it again to solve the problem, but the result is not guaranteed.
The black windows react to mouse clicks (and probably to keyboard input) as sometimes I got dialogs appeared on the screen, definitely as a result of my blind clicks.

Any ideas?

---

### Post by namnguyen on 2007-08-21
I got the same problem, the windows sometimes appear black
My laptop: Intel Core2Duo T7200, 2 GB DDRAM, NVidia GeForce Go 7200 256MB
any idea, please?

---

### Post by PenguinMafia on 2008-07-09
I also have this problem. It is very annoying because I can't find out what is happening.

---

### Post by VictorR on 2008-07-10
I don't use any virtualization software any longer, but I had experienced similar problem (my video card has only 64 MB). My opinion is that black windows appear when there is lack of video memory (when running Compiz-Fusion). In this situation Compiz can paint window borders, but can't do the rest. From my observation all Windows programs with Wine consume more video RAM, than native applications, so possibly, VMware server takes even more, leaving nothing to others.

I generally avoid this problem by disabling some VRAM-hungry effects (eg. transparent cube). Maybe there are some settings in VMware config, which may reduce video memory requirements, but I am not sure.

---


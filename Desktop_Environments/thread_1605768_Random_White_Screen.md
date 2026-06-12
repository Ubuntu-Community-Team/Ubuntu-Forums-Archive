---
title: "Random White Screen"
date: 2010-10-25
forum: Desktop Environments
---

### Post by oh beakes on 2010-10-25
Hi,
I'm new to ubuntu but I've installed ubuntu 10.10 on my desktop and it seems to work fine. But it keeps freezing up on me (sometimes a solid white screen, other times with vertical lines on a white background) and then becomes non-responsive. Sometimes there is a small (about 1in) square where the mouse was when it froze.

I have a fairly old computer (emachines T6522). Is there something I can do to keep it from crashing?

---

### Post by sikander3786 on 2010-10-25
Hi and Welcome to the forums :popcorn:

Which graphics card have you got? Did you install proprietary drivers for you card? Please provide you hardware specs as well.

Are you using compiz?

For troubleshooting on X freezes, see this page.

[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by oh beakes on 2010-10-26
CPU :	AMD Athlon™ 64 3500+ Processor
Chipset :	RS480 chipset
Memory :	1024MB DDR (2 × 512MB)
Hard Drive :	200GB HDD
Video :	ATI Radeon™® Xpress 200 (PCI-Express®®)
128MB DDR shared video memory

I reformatted and installed 10.10 on it, and haven't done anything else (I don't really know what I'm doing with it). Is there anything else I need to get this running?

---

### Post by sikander3786 on 2010-10-27
If you haven't installed the graphics drivers, installing them might solve the problem. Look under System > Administration > Additional Drivers and install the current version.

---

### Post by oh beakes on 2010-10-27
When I open up the additional drivers option I simply get a window telling me that "no proprietary drivers are in use on this system."

Do I need to find the driver somewhere online before it will come up there?

Thanks for your help.

---

### Post by aofc on 2010-10-31
I have the same problem, while I have been using 10.10 for about two months now (started with the release candidate), it was working fine until a few days ago when this started to happen. Maybe an update is causing the problem?

Also, I just switched to the beta Flash 64bit driver, and this problem started early after that, although I don't think they're related since I think this happened when I was not using any flash.

Ubuntu 10.10 64bit with latest updates (from Proposed rep)
CPU : Intel Core2 Duo T6600 2.20GHz
Memory : 4Gb
Video : Mobility Radeon HD 3400 series (with open source drivers)

And actually the system seems to be still running, only the video crashes, with a white screen or a what seems to be purple vertical lines on a white background. Keyboard is still responding (at least Caps lock) and music keeps playing. I can't seem to be able to switch to another session with Ctrl-Alt-F# though.

This happens every couple of hours.

---

### Post by Toadmund on 2010-10-31
Try disabling AMD 'cool 'n' quiet' in the BIOS.


[Read this]("http://ubuntuforums.org/showthread.php?t=420888&page=3")

(Pictures on page one)

---

### Post by Ingenium on 2010-12-29
I'm having a similar issue, but I'm not sure if it's the same or not. I attached a picture of what my screen looks like. I have a Thinkpad T400 with an Intel CPU, but ATI graphics. So there is no "cool n quiet" feature in the BIOS to disable. Anyone have any other thoughts?

---


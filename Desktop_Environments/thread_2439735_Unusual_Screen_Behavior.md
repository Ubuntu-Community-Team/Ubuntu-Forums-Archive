---
title: "Unusual Screen Behavior"
date: 2020-03-31
forum: Desktop Environments
---

### Post by and003 on 2020-03-31
Today I installed the new Ubuntu 19.10 operating system. The install went well, but I seem to have some unusual behavior. Small streaks have been popping up on my display. They show up, disappear, and come back again. Even though I can still use the computer, these streaks are a distraction that I would prefer not to deal with. 

I took a snapshot of these apparent streaks and attached it to this post to see if anyone can figure out what this is. This snapshot is from when I was using KDE Plasma, but these streaks have occurred in the Ubuntu desktop environment as well. Even though I intend to switch back to Ubuntu 18.04, I wanted to post this just in case someone had the same problem as I did. I have also reported this as a bug at the Ubuntu Launchpad forum.

[ATTACH=CONFIG]285358[/ATTACH]

---

### Post by Autodave on 2020-03-31
Some info on your hardware may help.

---

### Post by and003 on 2020-04-08
> **Autodave said:**
> Some info on your hardware may help.

Here is the hardware information you asked for.

Motherboard: MSI 970 GAMING DDR3 2133 ATX AMD
Processor: AMD FD8350FRHKBOX FX-8350 FX-Series 8-Core Black Edition
Memory: HyperX Kingston FURY 32GB (4x8GB) 1866MHz DDR3 CL10 DIMM - Black (HX318C10FBK2/16)
Video Card: EVGA 1GB GeForce 8400 GS DirectX 10 64-Bit DDR3 PCI Express 2.0 x16 HDCP Ready Video Card Model 01G-P3-1302-LR
Monitor: Acer V173 Djb 17-inch (LCD) 

Also, I installed Ubuntu 19.10 on my home theater PC and there were no streaks. My HTPC is hooked into my big screen TV through an HDMI cable, while my regular PC is hooked into the LCD monitor through a DVI-D cable.

---

### Post by lvm on 2020-04-09
If you are using nouveau display driver, replace it with nvidia driver.

---

### Post by and003 on 2020-06-18
LVM, even though I never had a chance to respond, I want to say thank you for the information.

---


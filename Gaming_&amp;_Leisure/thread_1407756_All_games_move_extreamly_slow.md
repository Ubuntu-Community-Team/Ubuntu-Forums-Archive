---
title: "All games move extreamly slow?"
date: 2010-02-15
forum: Gaming &amp; Leisure
---

### Post by hawaiian1der on 2010-02-15
[LEFT]The other day I installed a few games for Ubuntu from the Ubuntu Software Center. Games like Nexuiz, Blob Wars 1 and 2, Neverball, and Frets on Fire. All of these games and a few other move really slow no matter what I do. My graphics card is:  ATI Technologies Inc Mobility Radeon HD 3450, or at least thats what I think it is. I've looked all over forums, I look really badly, but I can't find anything that helps me solve my problem...[/LEFT]

---

### Post by Chesnut on 2010-02-16
What about your RAM (memory) and CPU (processor)? They also affect the speed/framerates of your games.

---

### Post by Ferrat on 2010-02-16
Do you have the latest ATi drivers active? sounds like you might be running the games in software render mode or something.

---

### Post by handy on 2010-02-20
The results of this command will provide you/us, with the info' telling if you have hardware or software OpenGL support:

glxinfo |grep -i opengl

If you don't have hardware OpenGL support, you probably need to install the AMD/ATi Catalyst proprietary driver, as at the moment, it still gives by far the best 3D (OpenGL) support.

---

### Post by hawaiian1der on 2010-05-19
> **handy said:**
> The results of this command will provide you/us, with the info' telling if you have hardware or software OpenGL support:

glxinfo |grep -i opengl

If you don't have hardware OpenGL support, you probably need to install the AMD/ATi Catalyst proprietary driver, as at the moment, it still gives by far the best 3D (OpenGL) support.

The results of that command are:

```
cameron@cameron-laptop:~$ glxinfo |grep -i opengl
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20091221 2009Q4 
OpenGL version string: 2.1 Mesa 7.7.1
OpenGL shading language version string: 1.20
OpenGL extensions:

```

As for RAM, I know I have 4GB of RAM, I don't know about the CPU or the drivers.

P.S. Sorry it took so long for this post.

---

### Post by achase79 on 2010-05-19
by your information it looks like either your video gfx are intel and not ati or you don't have the video drivers enabled.  Go to system->administration->hardware drivers and see if the ati proprietory drivers are installed and enabled.

---

### Post by Objekt on 2010-05-19
I think I see the problem.  It appears you're using one of the default, open-source ATI drivers, which is OK for 2D stuff (e.g. Web browsing) but usually stinko for 3D.

For some reason, your hardware is reading as an Intel GMA chipset instead of a Radeon HD.  Not sure why that's happening.

It will probably solve your problem if you just install the proprietary ATI driver package.

I'll have to post details later, as I'm not at my Ubuntu machine now.  Or, you can search for how to use the "Hardware Drivers" applet built into Ubuntu.  It is buried somewhere in the "System" menu.  I expect that will fix you up, although there are exceptions.

---

### Post by del_diablo on 2010-05-19
> For some reason, your hardware is reading as an Intel GMA chipset instead of a Radeon HD. Not sure why that's happening.

Its likely a dual-laptop armed with 2 chipsets, i got one like it myself. Its complely idiotic.
If the BIOS is well written it is possible to run select GPU to run, switch the computer from portable to performance with a button somewhere.

---

### Post by hawaiian1der on 2010-05-22
> **del_diablo said:**
> Its likely a dual-laptop armed with 2 chipsets, i got one like it myself. Its complely idiotic.
If the BIOS is well written it is possible to run select GPU to run, switch the computer from portable to performance with a button somewhere.

I'm going to go with your suggestion? :P
To make things easier here:

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```

---


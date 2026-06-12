---
title: "How to Change Display Resolution, Not Auto Detect"
date: 2012-12-05
forum: Desktop Environments
---

### Post by juanbisente on 2012-12-05
I have installed ubuntu 12.04 and I can't change my display resolution.It only has 1024x768 and 800x600 choices. I have a SynchMaster CX791N monitor. but if I plugged an SynchMaster Crt monitor my display has lot of resolution choices.

I have tried to manually add in xrandr but it has an error saying
> xrandr: Failed to get size of gamma for output defaultplease help
thanks

---

### Post by grahammechanical on 2012-12-06
I have a SyncMaster T200HD. The operating system reads the Extended Display Identification Data (EDID) that is stored in the monitor and uses that to run the monitor at the optimum settings decided by the manufacturer. Running a modern monitor at a setting other than the optimum setting increases the risk of damage to the monitor. This is one reason why we do not get a display utility that allows us (the user) to pick and choose what settings the monitor should be run at.

> Extended display identification data (EDID) is a data structure provided by a digital display to describe its capabilities to a video source (e.g. graphics card or set-top box). It is what enables a modern personal computer to know what kinds of monitors are connected to it.

[http://en.wikipedia.org/wiki/Extended_display_identification_data]("http://en.wikipedia.org/wiki/Extended_display_identification_data")

Cathode Ray Tube (CTR) monitors could be run at a range of settings with no risk of damage so long as we did not try to run the monitor at a setting greater than the maximum specified by the manufacturer.

I used to have a CTR monitor that had a maximum setting of 800 x 600 pixels at 60 Hz. But the computer's video card could give out much higher settings which would have damaged the monitor

In those days the user had to choose a setting at installation time and could change the setting after installation. Now, it is all done for us.

Regards.

---

### Post by dannyboy79 on 2012-12-06
what video card do you have?

lspci

---

### Post by juanbisente on 2012-12-07
I don't have video card

lspci result
> 
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 IDE Controller (rev 01)
00:03.0 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)


---

### Post by dannyboy79 on 2012-12-07
if you didn't have a video card then you wouldn't get any display at all. LOL  You have a Sis onboard video chipset (basically a video card) You'll need to google SiS 771/671 to find out if there's anything special to do to get better resolutions in Ubuntu with that video chipset. I can't help sorry, good luck

---


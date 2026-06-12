---
title: "Problem with Desktop Effects"
date: 2007-06-05
forum: Desktop Effects &amp; Customization
---

### Post by kaputstyle on 2007-06-05
Hello, i've read a bunch of articles on trying different things to get them to work.  When I try to enable them i get an error saying it cannot enable it.  At first all i got was a total white screen, hitting esc removed it.  Then I decided to just let it run..after a while it went back to the desktop and the same window was showing saying "enable desktop".  I installed the emerald theme manager and i think i got the xgl isntalled...also installed the synaptic manager.  Now i don't get the white screen just the error saying it can't enable it.  All of the components in my computer a pretty new... my video card is integrated into my motherboard.  I'm pretty new to linux.  Here is my mother board specs.

I set it up to be vista ready...however I do not wish to get vista lol

Model
Brand 	BIOSTAR
Model 	P4M800 Pro-M7
Supported CPU
CPU Socket Type 	LGA 775
CPU Type 	Pentium D / Pentium 4 HT / Celeron D
FSB 	1066/800MHz
Supported CPU Technologies 	Hyper-Threading Technology
Chipsets
North Bridge 	VIA P4M800 PRO
South Bridge 	VIA VT8237R
Memory
Number of Memory Slots 	2×240pin
Memory Standard 	DDR2 533
Maximum Memory Supported 	2GB
Expansion Slots
AGP Slots 	1 x AGP 4X / 8X
PCI Express x16 	None
PCI Slots 	3
Other Slots 	1 x CNR
Storage Devices
PATA 	2 x ATA100 up to 4 Devices
SATA 1.5 Gb/s 	2
SATA RAID 	0/1
Onboard Video
Onboard Video Chipset 	S3 Graphics UniChrome Pro IGP
Onboard Audio
Audio Chipset 	Realtek ALC655
Audio Channels 	6 Channels
Onboard LAN
LAN Chipset 	Realtek 8201CL PHY
Max LAN Speed 	10/100Mbps
Rear Panel Ports
PS/2 	2
COM 	1
LPT 	1
Video Ports 	D-Sub
USB 	4 x USB 2.0
Audio Ports 	3 Ports
Onboard USB
Onboard USB 	4x USB 2.0
Physical Spec
Form Factor 	Micro ATX
Dimensions 	9.6" x 8.6"
Features
Power Pin 	20 Pin

---

### Post by orb9220 on 2007-06-05
> Onboard Video Chipset S3 Graphics UniChrome Pro IGP

Is this the video you are using? If it is that is why you are having problems.

To run desktop effects you need to check if that chipset is supported for compiz/beryl.

---

### Post by kaputstyle on 2007-06-06
I found an old AGP gigabyte gv-r70647 radeon 7000 video card laying around... I popped it in.  I got the desktop effects to work... then I tried to install beryl.  I had problems even getting to the windows - stuck in what resembles DOS to me lol (remember i'm a newb to linux)...while bouncing from forum to forum...and reading numerous how to's..I kept coming up empty with the same old error everyone else is. "No Screen Selected" and "unable to parse xconfig"  After messing around for hours with it...I noticed something odd.  Said there was a problem with touchpad...  so i got into the xconf file and decided what the heck and get rid of that line...when i restared bang everything popped up ok..working good now...hopefully beryl will install ok 

So anyone still having problems maybe try taking out touchpad?  worked for me... said something like it was not identified?  anyway i'll worry about that later.

---


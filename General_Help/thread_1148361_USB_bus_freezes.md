---
title: "USB bus freezes?"
date: 2009-05-04
forum: General Help
---

### Post by jim-bob on 2009-05-04
Hey!

I've got an ASUS MB M3N78 PRO with an AMD Phenom Quad-Core Processor and three devices on USB: a printer, a flat bed scanner and a TV-DVB-box.

When I'm printing a few pages (>5) or use w_scan to scan the TV-channels it seems that the USB-bus freezes. The rest of the system works fine but no USB-device works anymore. I tried to unload the USB-modules but that didn't succeeded. The only solutions seems to be to reboot.

It's the same with ubuntu 8.10, mythbuntu 9.04 (32bit & 64bit) I tried even openSuSE.

Any hint and help to solve that annoying problem would be greatly appreciated.

Best regards 
Jim Bob

---

### Post by Bindsa on 2009-05-04
Look into your BIOS settings, e.g. try loading optimized defaults, I guess your problem lays in your BIOS configuration, not sure though.

---

### Post by jim-bob on 2009-05-05
Thank you, I will do that. But - what to look for? As far as I remember there is nothing else than enable/disable USB? What should I change? I guess I've allready set the optimized defaults, but I will look for that this evening.
Do you want me to post any informations from the BIOS?

---

### Post by jim-bob on 2009-05-05
The only thing I can change in the BIOS (for USB) is enable/disable USB or the USB legacy support. I have disabled now the lagacy support but it didn't helped. :-(

w_scan again hangs on the first channel.

IS THERE ANYBODY WHO CAN HELP ME?

the output of lsusb is:
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 062a:0000 Creative Labs Optical mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 0b48:1004 TechnoTrend AG TT-PCline
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

lspci:
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP78S [GeForce 8200] High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP78S [GeForce 8200] Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:12.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:13.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:0a.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8300 (rev a2)

---

### Post by dabl on 2009-05-05
> **jim-bob said:**
> The only thing I can change in the BIOS (for USB) is enable/disable USB or the USB legacy support. I have disabled now the lagacy support but it didn't helped. :-(

w_scan again hangs on the first channel.

IS THERE ANYBODY WHO CAN HELP ME?

the output of lsusb is:
[COLOR="Red"]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]
Bus 004 Device 002: ID 062a:0000 Creative Labs Optical mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR="Red"]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]
Bus 003 Device 002: ID 0b48:1004 TechnoTrend AG TT-PCline
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




I'll stick my neck out and suggest that two "root hubs" can't have the same device ID and live happily together.  :frown:

---

### Post by jim-bob on 2009-05-06
Allright, that's a hint! Thank you!
Is there a way to change this in ubuntu or do I have to disable one root hub in the BIOS / motherboard (if this is possible)?

---

### Post by dabl on 2009-05-06
Did you build this system?  No offense -- it's just a curious and unusual error, and kinda looks like mis-wired hardware.  I just now noticed that the "Device 001" IDs are also the same!  There is something very odd in the USB hub on that system -- redundancy of buses and devices.

---

### Post by Maheriano on 2009-05-06
Universal Serial Bus bus?

---

### Post by jim-bob on 2009-05-06
@ dabl
Yes, I build this system. But there are no wires, switches or anything else. There are just six USB-Ports on board (and three connectors more you can use with a cable and a USB-module which I did not).  I opened it again to look for it and read the User Guide. In the BIOS there is nothing to switch except enable/disable USB 2.0. 

Is there a way to give the devices an unique ID? 
Who did it? The BIOS? 

BTW: What does that 
*Linux Foundation 1.1 root hub*
mean? There should be no USB 1.1 - only USB 2.0?

@ Maheriano
Thank you.

---

### Post by dabl on 2009-05-06
I built a couple of Asus systems recently, but the motherboards were not your model -- they were in the P5Q family for Intel CPUs.  So, I'm just guessing at the nature of the problem, based on your description.

You said "six" onboard ports, but it appears there are both USB 1.1 and USB 2.0 ports connected.  Take a look at the motherboard manual (get a bright light and a magnifying glass ...) -- I think maybe you could connect your internal front-panel wiring only to the USB 2.0 header, and then use BIOS to enable 2.0, and usually that means a USB 1.1 device will also work at the slower transfer speed.

---

### Post by jim-bob on 2009-05-07
I'm not longer so sure now about that ID thing...
I've got another system (a VIA board) with ubuntu 7.10 with only one USB port in use.
Here is the lsusb:
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 15ca:0101  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  

BUT when I start the 9.04-CD on that system and do the lsusb I get THIS:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 15ca:0101 Textech International Ltd. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

So it seems that is just a new way to print the formerly 0000:0000 device ID?

Hey, I've watched the X-Files - I know the truth is out there!   ;-)
So what's wrong here?

---

### Post by strange on 2010-05-25
i have a asus motherboard as well with nvidia 8200 chipset and have the same problem

[http://www.nvnews.net/vbulletin/showthread.php?t=135022](http://www.nvnews.net/vbulletin/showthread.php?t=135022)

its not just us its the chipset and there seems to be no actual fix for it as of yet :(

---

### Post by uBeer on 2011-03-29
It's a bit late, but I've found a solution that seems to work for me:
In the bios there is a setting where you can turn of something like: oiahci. With upgrading to a new processor I loaded the optimal settings and it switched this on and ruined my USB experience on linux (not on windows). Hope this can help anyone looking for the same bug!
I don't know exactly what it does, so be careful... I'm just happy that I can listen to music again without problems!

---

### Post by save2 on 2013-04-21
I tried all kind of workarounds (none worked for me) .what worked for me is simply buy a PCIe USB card

[http://ubuntuforums.org/showthread.php?t=2136506&p=12612114](http://ubuntuforums.org/showthread.php?t=2136506&p=12612114)

---

### Post by oldos2er on 2013-04-21
Closed, please don't bump old threads.

---


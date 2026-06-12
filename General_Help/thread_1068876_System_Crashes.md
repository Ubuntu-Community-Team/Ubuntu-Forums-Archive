---
title: "System Crashes"
date: 2009-02-13
forum: General Help
---

### Post by Haruki-kun on 2009-02-13
Ubuntu crashed on me about two weeks ago. Like [this.]("http://i163.photobucket.com/albums/t288/Vaarsuvius89/img_0064.jpg") I rebooted and it seemed fine, so no problem.

Two weeks later, last night, it crashed again. I was starting to get worried, but I switched it off and restarted, then went on working.

Just now, I turned it on again. Just as the system booted and I started reaching for the Applications menu, it happened again.

Why is this happening? Did I just come across a Linux Blue Screen or something? Is it a Software problem or a Hardware problem? Please help me.

---

### Post by unixeducation on 2009-02-13
This looks like an issue with the display driver. What graphics chipset and Xorg version are you using? Do you have visual effects turned on?

---

### Post by Haruki-kun on 2009-02-13
> **unixeducation said:**
> What graphics chipset and Xorg version are you using?

I'm not sure. I'm really new at this. How or where can I find out?

> Do you have visual effects turned on?

Compiz Fusion.

EDIT: Wait, I think it is nVidia GeForce 7000M. Is that what you meant?

---

### Post by unixeducation on 2009-02-13
Everyone is new at some point :). You can use the "lspci" command to get a listing of various devices installed in your system. Please run this in a shell and paste the output into a reply. As for Xorg, you can run "X -version" to find the version.

You might also have RAM issues. You could try booting up with an Ubuntu CD and running the memory tester for an hour or so to see if it finds anything.

---

### Post by Haruki-kun on 2009-02-13
Result of lspci:
> 00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


Result of X -version:
> This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux haruki-laptop 2.6.24-23-generic #1 SMP Mon Jan 26 00:13:11 UTC 2009 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present


---

### Post by dannyboy79 on 2009-02-13
I am still using Feisty so if none of this applies I apologize in advance.

this should tell us what driver you're using within your xorg.conf file

```
cat /etc/X11/xorg.conf | grep Driver
```

then paste the output back here.

this will tell us what graphics card you have.

```
lspci
```

paste the output here as well.

---

### Post by Haruki-kun on 2009-02-13
> **dannyboy79 said:**
> this should tell us what driver you're using within your xorg.conf file

```
cat /etc/X11/xorg.conf | grep Driver
```

Result:

> 	Driver		"kbd"
	Driver		"mouse"
	Driver		"synaptics"
	Driver		"nvidia"


---

### Post by unixeducation on 2009-02-13
Do you have the restricted driver enabled for your card? Sometimes this helps, sometimes it hurts... it's worth a shot enabling/disabling it in any event.

Another option is downloading drivers directly from NVIDEA: [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

---

### Post by unixeducation on 2009-02-13
> **dannyboy79 said:**
> I am still using Feisty so if none of this applies I apologize in advance.

this should tell us what driver you're using within your xorg.conf file

```
cat /etc/X11/xorg.conf | grep Driver
```

then paste the output back here.

this will tell us what graphics card you have.

```
lspci
```

paste the output here as well.

For X, "X -version" gives much better information.

---

### Post by Haruki-kun on 2009-02-13
> **unixeducation said:**
> Do you have the restricted driver enabled for your card? Sometimes this helps, sometimes it hurts... it's worth a shot enabling/disabling it in any event.

Another option is downloading drivers directly from NVIDEA: [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Well, I never downloaded them directly from nVidia. I think I used the restricted one. Is it the one that was under "Hardware Drivers"? I just enabled it, then the computer downloaded it and it's been working like that ever since.

---

### Post by unixeducation on 2009-02-13
This may not be the most encouraging answer, but I've had machines that just wouldn't run reliably with Compiz effects. You may have better luck with freshly installed drivers from NVIDEA, or you may have to turn off the accelerated driver entirely.

---

### Post by Haruki-kun on 2009-02-13
> **unixeducation said:**
> This may not be the most encouraging answer, but I've had machines that just wouldn't run reliably with Compiz effects. You may have better luck with freshly installed drivers from NVIDEA, or you may have to turn off the accelerated driver entirely.

...<.<

I can't. I'm a digital art student, I need my graphics. >.<

I'll try nVidia drivers, then.

---

### Post by dannyboy79 on 2009-02-13
I wouldn't think that he wants to turn off the accelerated drivers, he would want to turn off compiz fuzion. that's what's causing the crashing I am guessing. compiz is very ram and graphics intensive.

---

### Post by unixeducation on 2009-02-13
That's what I suggested earlier in this thread, but I don't have any info on whether he's tried that route or not.

---


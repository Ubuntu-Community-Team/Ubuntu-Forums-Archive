---
title: "Emachines M5414 Video Issues (Ubuntu 9.04)"
date: 2009-05-06
forum: General Help
---

### Post by jimloomis on 2009-05-06
Hey guys,

I'm using an Emachines M5414, just installed 9.04, and I'm having issues with the video. Artefacts appear in highly detailed images and in other random parts of the screen (these are stray pixels that deviate or blink to colours that aren't supposed to be displayed). The computer is still usable, but being that I use this for imaging, I need this problem solved.

Things I've noticed/tried:
-Ubuntu can't detect the monitor using "Display Settings", so it might be hardware issues related to the monitor and not the video card.
-I tried changing Xorg to a different configuration to see if it would help, nothing changed.
-I changed the shared video memory in BIOS from 64mb to 128mb, still no change.
-I notice a firmware warning when shutting down/restarting the computer, but can't tell what it is for as it only appears for a split second.
-The video worked perfectly in 8.04, why would Jaunty be any different?

I sent a request to launchpad and have posted about this before... any ideas? 

PLEASE HELP!
-Jim

---

### Post by cariboo on 2009-05-06
It would help if you told us what video chipset your computer uses.

To view the firmaware message, check dmesg. Either open an Applications-->Accessories-->Terminal and type:

```
dmesg | less
```

or go to System-->Administration-->Log File Viewer.

I get this messagte at startup:

```
Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI _PSS objects in a way that Linux understands. Please report this to the Linux ACPI maintainers and complain to your BIOS vendor.
```

It doesn't affect the operation of my computer. The only way to repair it is with a BIOS update, and I'm already using the latest. I've already gone through this with one of the kernel devs and it comes down to a problem the the motherboard manufacturer has to repair.

---

### Post by jimloomis on 2009-05-06
Hey!

Thanks for the reply! Here's what I get using the command you gave:

   0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000027fd0000 (usable)
[    0.000000]  BIOS-e820: 0000000027fd0000 - 0000000027fde000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000027fde000 - 0000000028000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
:

I hope this helps!

---

### Post by Yellow Pasque on 2009-05-06
There are a lot problems with Intel video chips in Jaunty. (I'm assuming you have Intel video).

> The video worked perfectly in 8.04, why would Jaunty be any different?
Jaunty uses an updated kernel, Xserver, Intel driver...

---

### Post by jimloomis on 2009-05-06
I noticed that, but being that I have an AMD Sempron processor, could I really have an Intel video chip? I guess anything is possible, but I always assumed that AMD would go with a generic brand or ATI.

I'll browse the Intel video issues in the meantime. Anyone care to point to a specifically helpful thread?

Thanks.

---

### Post by Yellow Pasque on 2009-05-07
If you have an AMD processor, you probably don't have Intel video.
Use this command to figure out what video you have:
```
lspci
```
Other helpful commands that may revel issues:
```
LIBGL_DEBUG=verbose glxinfo
cat /var/log/Xorg.0.log
```

---

### Post by jimloomis on 2009-05-09
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

That is my video card, but upon further inspection after plugging my laptop into my computer monitor, I realized that it must be an issue with monitor support and not the video card, as no artefacts appeared on the external display.

How can a force Ubuntu to detect my monitor or work with it to avoid the display of artefacts?

I would post the results of the log output, but it is too long. Let me know if you guys want/need to see it.

Thanks!

---

### Post by swaaye on 2009-11-09
I just had to reply to this because I just spent a few hours troubleshooting this problem with a Emachine M5414 notebook.

The crazy wrong/flashing colors were caused by incorrect LCD detection. After scouring the SiS driver page, I found an option called PanelDelayCompensation. Setting this to "4" in xorg.conf fixed it up.

[http://www.winischhofer.eu/linuxsispart2.shtml#pdc](http://www.winischhofer.eu/linuxsispart2.shtml#pdc)

---

### Post by jimloomis on 2010-02-20
Thanks for the reply!

No luck on finding that function you were talking about when I pull up xorg.conf. How/where do I change that value?

---


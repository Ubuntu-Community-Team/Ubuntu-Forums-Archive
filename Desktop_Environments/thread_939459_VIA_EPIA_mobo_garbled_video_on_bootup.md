---
title: "VIA EPIA mobo garbled video on bootup"
date: 2008-10-05
forum: Desktop Environments
---

### Post by wildyoot on 2008-10-05
Hello,

I have a machine with a VIA EPIA-ME6000 Mini-ITX board running Ubuntu 8.04.1. If left to its default bootup routine with kernel 2.6.24-19, the video mode will switch to random blue characters so that it is impossible to log-in or use the recovery mode. If I exit to GRUB and select kernel version 2.6.22-14, it works, so this is what I have been doing for some months. 

Has anybody seen this before? Should I bother trying to fix this, or should I set the default bootup kernel to the -14 version since it works (I assume one can do that with GRUB)? Is there anything I should be concerned about missing by using an older kernel?

Thank you for any help. I always use ubuntuforums search facility to find solutions but in this case I am stumped.

---

### Post by overdrank on 2008-10-06
> **wildyoot said:**
> Hello,

I have a machine with a VIA EPIA-ME6000 Mini-ITX board running Ubuntu 8.04.1. If left to its default bootup routine with kernel 2.6.24-19, the video mode will switch to random blue characters so that it is impossible to log-in or use the recovery mode. If I exit to GRUB and select kernel version 2.6.22-14, it works, so this is what I have been doing for some months. 

Has anybody seen this before? Should I bother trying to fix this, or should I set the default bootup kernel to the -14 version since it works (I assume one can do that with GRUB)? Is there anything I should be concerned about missing by using an older kernel?

Thank you for any help. I always use ubuntuforums search facility to find solutions but in this case I am stumped.

Hi and welcome, have you tried using the xfix option when booting into recovery mode on the 24-19 kernel? What is the model of the graphics?

---

### Post by wildyoot on 2008-10-08
> **overdrank said:**
> Hi and welcome, have you tried using the xfix option when booting into recovery mode on the 24-19 kernel? What is the model of the graphics?

Hello and thank you,

I have tried to run xfix but since the screen is garbled I am guessing at the right keystrokes (3 arrow keys down, then Enter?). This did not appear to solve anything however (assuming it ran xfix).

Here is the lshw output for the display hardware (although I have to do this from the older kernel):

```
*-display
                description: VGA compatible controller
                product: VT8623 [Apollo CLE266] integrated CastleRock graphics
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 03
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
                configuration: driver=vt8623fb latency=32 mingnt=2 module=vt8623f
```

---

### Post by wildyoot on 2008-10-16
A fresh install of 8.0.4.1 fixed the problem.

Still shows a flash of garbled blue screen and characters on boot up, but the login screen appears right after now. Possibly it was crashing at that point before. So looks like something got upset during the -14 to -16 kernel upgrade.

Thanks for the help.

---


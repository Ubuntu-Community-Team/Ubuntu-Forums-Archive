---
title: "Ubuntu 18.04 problems on boot - no wifi, screen color management issues"
date: 2018-08-16
forum: Desktop Environments
---

### Post by peter-a on 2018-08-16
Hello,

When I boot my 18.04 PC (18.04.1 Gnome 3.28.2 all up to date) I get the following issues, not all of the time, but most of the time.

Wifi is active but sees only my usual network and doesn't connect to it. Turning wifi off and back on again fixes the problem.

Display color management is wrong, showing heavy blue tinting on both my monitors. If I go into the displays control panel, turn color management off and back on again, the display color is correct.

My primary display shows a blank screen with a 'resolution out of range' message. If I either change the display size in the control panel, or turn the monitor off and back on, it's fine.

I thought there might be a problem with my SSD or hard disk not making config files available at boot so I added a 2 second delay into grub to allow the disks to get up to speed, but that makes no difference.

dmesg shows some drive errors on sdd and sde:

[   14.658222] sd 7:0:0:0: [sde] No Caching mode page found
[   14.658223] sd 7:0:0:0: [sde] Assuming drive cache: write through


But these are just USB sticks. No other errors are in the dmesg log.

The system boots from a SSD and that's where Ubuntu and my home directory both are. All my data files are on a HDD. Disks says that all my disks are 'OK'.

The fact that this happens often but not always says this is not a config issue or corrupted profile file because my feeling is that would cause a consistent problem. The intermittent nature suggests hardware.

Where can I look next to find the source of this odd problem?

thanks

Peter

---

### Post by Autodave on 2018-08-17
Is this a laptop or desktop?  If desktop, have you made sure that all in ternal connections are clean and secure?

---


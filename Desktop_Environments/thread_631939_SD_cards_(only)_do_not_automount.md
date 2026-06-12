---
title: "SD cards (only) do not automount"
date: 2007-12-04
forum: Desktop Environments
---

### Post by kenryan on 2007-12-04
Hello!

I seem to have lost the ability to automount SD cards from my multicard readers.

The main card reader in question is one of these multiple-slot readers that mounts in a drive bay.  It has the Best Buy "Dynex" brand, and lsusb reports Alcor Micro Corp.  Identical behavior is observed with a Sandisk MultiMate SD+ reader and another no-name reader (which only supports CompactFlash, SmartMedia and SD).

When I insert an SD card, the card gets recognized by the kernel drivers but it does not pop up a window on the Gnome desktop.  CompactFlash, SmartMedia, and MicroSD cards pop up fine.  Other USB drives also pop up fine.

As best I can tell, the point where I lost the auto-popup of the SD cards was when I upgraded from 6.10 to 7.04 (this is the x86 32-bit version, running on a 3GHz P4 CPU).  It worked fine under 6.10, did not work under 7.04.  I shortly thereafter upgraded again to 7.10, hoping the problem would go away.  It has not.  In both cases I used the Update Manager while logged in as root to do the upgrade, and accepted all of the default offerings.  I have not yet discovered anything else broken by the upgrades (multimedia and ipod stuff still works fine).

I can manually mount the SD card and access it.  It just does not seem to get recognized and mounted by whatever mechanism the default gnome environment uses to pop up file browsers for inserted media cards.

I have tries multiple cards of different capacities; 256MB, 1GB, 2GB (none are SDHC).  All are Sandisk-brand.

Interestingly, one of the SD cards is the Ultra II Plus USB - the one that snaps in half to reveal a built-in USB connector.  When that is inserted into a front-panel USB port it also refuses to automount.  A Sandisk Cruzer Micro 512MB thumb drive works fine in the same port.

My system seems to have something against full-size SD cards (remember the microSD works).

I'm baffled and have no idea what to check next.

BTW, another thread said to ensure dbus-x11 is installed.  It is, and the machine was rebooted since.

Thanks in advance for any ideas!

    ken

---


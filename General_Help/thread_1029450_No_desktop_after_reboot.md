---
title: "No desktop after reboot"
date: 2009-01-03
forum: General Help
---

### Post by backbackheyhey on 2009-01-03
When I boot version 8.10 from a live CD, it appears to work normally.  When I install it with Wubi (both with and without an iso in the Wubi directory), I reboot after the Windows phase of the installation, and instead of the desktop or any apparent continuation of the installation process, I get the following:

[COLOR="Red"]Loading, please wait...

BusyBox v1.1.02 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _
[/COLOR]
The underscore character at the end of the last line is a blinking cursor.  I left it alone for approx. 10 min., and there was no disk activity or any other sign that the machine was doing anything, but it was not frozen.  I was able to type commands (after leaving it alone for 10 min.), and it responded.

I am running the following:

Dell Dimension 4600
2.6 GHz Intel Pentium 4
1 GB RAM
111 GB Hard Drive w/NTFS (72 GB free before installation)
NVIDIA GeForce FX 5200 w/128 MB of RAM
Windows XP Home Edition Service Pack 3

I defragged and ran chkdsk /r before installation.  I've also tried booting in normal mode, in safe graphic mode, with ACPI workarounds, and the Read-Only Demo.  I also tried installing from a CD (both version 8.10 and 8.04).

Any suggestions would be greatly appreciated.  Thanks.

---


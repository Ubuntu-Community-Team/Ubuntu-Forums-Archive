---
title: "High Speed USB disk mounting problem in Kubuntu."
date: 2007-10-07
forum: Desktop Environments
---

### Post by Caysho on 2007-10-07
VT82xxxxx High Speed USB PCI card (there's two firewire ports on it as well).
Kubuntu Dapper on Intel EPEA2 board (yes, an old board).  Updates are current.

In short:
When a disk is inserted into a High Speed USB port, the mounting dialogue may stay on screen a long time, or not go away until the disk is re inserted.  If cancel is selected, further disk insertions don't do anything.  This only occurs on High speed ports.

Detail:
When a usb disk is inserted, it goes through the normal process - I have it open the drive from the dialogue that appears.
Konqueror appears, pointing at /media/sda1 and the list of files shows up.
There is also a "Mounting /dev/sda1" dialogue that appears at the same time, but doesn't go away.
If the Konqueror window is closed, and the desktop drive icon "safely removed" via the icon's context menu, the mounting dialogue may go away.
If the disk is inserted again, the dialogue does go away.

If "cancel" is selected from this dialogue, then the Konqueror window still opens but nothing is shown.  The disk can be safely removed, but cannot be mounted again, no matter which usb port is used.

From a fresh boot, if a low speed USB port is selected, the mounting dialogue appears and completes/disappears.  There is no delay.

I think restarting X cleans up the problem, so it might be a KDE issue.

I figure this is a bug report, but I'm not clear on which part of the system is causing the problem.  Also, I can't find an instance of someone else having the same problem.

Prior to this, there was a problem with a usb hub I'm using that wasn't always being detected.  I found a solution was to add the following to /etc/modules

ehci_ucd 
uhci_ucd

---


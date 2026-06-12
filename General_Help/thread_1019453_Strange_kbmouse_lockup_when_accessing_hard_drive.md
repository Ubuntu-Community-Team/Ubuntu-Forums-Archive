---
title: "Strange kb/mouse lockup when accessing hard drive"
date: 2008-12-23
forum: General Help
---

### Post by RickPJ on 2008-12-23
I'm getting complete lockup of mouse & keyboard when doing high-volume disk reads on the 2nd IDE channel - very weird.

This is my faithful self-build desktop that I've recently installed Intrepid on, and that's been happily running XP for ages (trying to throw off the M$ shackles!). It's an oldish MB that uses a VIA KT266A Chipset. It's got 2GB RAM, 3 HDs and DVD writer. Mouse & KB are PS/2.

The HDs on IDE-2 are used for a lot of media, including DV editing, so have some very large files. I've found that anything that involves reading high volumes from these drives will cause the mouse and keyboard to freeze. A reset is needed to get out of it. Typical activity to cause it: copying a large media file, or fast scrubbing through a video when editing it, etc. The system itself doesn't hang, e.g. a file copy will complete even though mouse/kb input has died.

Reading the equivalent volume of data from a drive on IDE-1 doesn't exhibit the problem.

I have tried swapping all kinds of things around, including changing the IDE cable. I also ran memtest86 for several hours without error. I've eventually configured the boot drive on IDE-2, and the media drives on IDE-1. This is working so far, but I can still create the problem if I copy a large file from the system drive (which is now IDE-2) - which also confirms that it is a problem with IDE-2, and not individual drives.

I'm not comfortable with this, because at any time there might be some intense disk I/O on the system drive - which also has the swap partition.

This same hardware has been used with Windows XP for years without ever showing any problems, so somehow it looks like a driver compatibility or conflict issue to me. The behaviour is rather as if activity on IDE-2 causes a mouse interrupt to be lost, and the driver never recovers.

IRQ assignments are standard: KB IRQ-1, mouse IRQ-12, IDE-1 IRQ-14, IDE-2 IRQ-15.

Any ideas? How do I even start debugging this? :confused:

TIA
Rick

[ I originally posted this in the "hardware" forum, but on reflection I don't think it was the right place ]

---


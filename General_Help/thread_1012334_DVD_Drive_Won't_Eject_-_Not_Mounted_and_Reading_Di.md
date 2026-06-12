---
title: "DVD Drive Won't Eject - Not Mounted and Reading Disc"
date: 2008-12-15
forum: General Help
---

### Post by [TCK] on 2008-12-15
While attempting to read a DVD data disc while mounted Dolphin (KDE file browser) wouldn't see anything on the disc.  I pressed the unmount button, which worked except for the fact that the DVD drive read indicator is continually flashing.  Any attempts I've tried to eject the drive/stop reading have failed.

I've had this happen to me in the past with various DVDs and the only way I've managed to get the DVD drive fully functional is a hard reset.

Things I've tried (thanks to searches of various similar topics):

**Ctrl+Alt+Backspace**
Logged back in, no change.

**terminal command: eject/eject -t /dev/cdrom**
terminal hangs for about five minutes, reporting no error.  DVD drive still reads.

**terminal command: sudo fuser -k /dev/cdrom **
No error messages, but the DVD drive still reads.

**terminal command: sudo lshw -C disk**
terminal outputs "PCI (sysfs)" for a few seconds, then "SCSI", which it continues to display indefinitely. 

**terminal command: dmesg**
terminal outputs multiple pages, but nothing seemingly of worth.

**terminal command: sudo umount /dev/cdrom**
terminal outputs "umount: /dev/cdrom: not mounted"

**The paperclip method**
Getting the disc out works, but the DVD drive is still unusable (won't remount, eject).

The disc itself should be okay, I've tried it on a Windows system minutes earlier and it works perfectly.

Of note: I'm using Kubuntu 8.10, but I'd like to think that it's not the source of the problem, not to mention I'm trying to get this sorted through CLI.  I also think this is new since Intrepid.

---


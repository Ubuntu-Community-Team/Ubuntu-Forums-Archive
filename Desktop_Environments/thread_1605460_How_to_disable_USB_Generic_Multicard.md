---
title: "How to disable USB Generic Multicard?"
date: 2010-10-25
forum: Desktop Environments
---

### Post by tripzilch on 2010-10-25
Hi, I have a Medion Akoya E1212 netbook (which is an ALDI rebrand of the MSI Wind netbook) and naturally I'm trying to get the longest battery life possible :)

Already running Ubuntu (Lucid) Netbook Edition (though Moblin seems interesting too) and of course keeping a close look at **powertop**.

One of the things powertop can do, is disable unused USB devices [with the 'U' key]. There is, however, one persistent USB device that keeps popping up in powertop's list no matter how often I press 'U': my SD-card drive (which is apparently internally connected via USB). And it appears in the list regardless of whether I have inserted an SD-card in it or not.

When I use Nautilus to navigate to **computer://**, I can see the SD-card drive as an icon named "USB Generic Multicard", sitting next to my internal harddisk. I can rightclick and "eject" it, causing the icon to disappear, and the entry in powertop's list disappears as well.

My question, is there a way to make sure that the "USB Generic Multicard" USB device doesn't mount at all during startup? [Or, preferably that it detects whether an SD card it present (rarely) to decide whether to mount or not].

And if anyone knows the command-line command to "eject" the USB Generic Multicard device, that would also be great cause it would save me starting Nautilus every time (which is slow).

---

### Post by amlamarra on 2011-01-05
I have that same device showing up on my Toshiba NB305, except I'm running Windows 7...  It just started showing up after I plugged in a Western Digital "My Passport" 1 TB external hard drive.  I can disable the device, but it'll just come back if I try to uninstall it.  Strange.

---


---
title: "Drive /dev/hdg does not contain audio files"
date: 2008-05-10
forum: Desktop Environments
---

### Post by labinnsw on 2008-05-10
I get this pop up error soon after booting up my computer and it does not matter what I am doing.

If I select my CD ROM or DVD ROM, I also get the same message.

The CD ROM and a small hard drive is connected via a Highpoint RocketRaid 454 controller card. While the DVD ROM and the hard drive I boot from is connected to an IDE port. My motherboard is an Asus P5K SE. I am running Hardy Heron which I installed after making the CD.


Another error message I receive is:

DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

I can´t seem to replicate this one and I have not seen it this morning.

My System logs 10 error messages/second. An excerpt is below:

May 11 10:37:05 username-desktop kernel: [ 6066.057766] hdg: status error: status=0x58 { DriveReady SeekComplete DataRequest }
May 11 10:37:05 username-desktop kernel: [ 6066.057773] ide: failed opcode was: unknown
May 11 10:37:05 username-desktop kernel: [ 6066.057818] hdg: status error: status=0x58 { DriveReady SeekComplete DataRequest }
May 11 10:37:05 username-desktop kernel: [ 6066.057827] ide: failed opcode was: unknown
May 11 10:37:07 username-desktop kernel: [ 6068.054184] hdg: status error: status=0x58 { DriveReady SeekComplete DataRequest }
May 11 10:37:07 username-desktop kernel: [ 6068.054191] ide: failed opcode was: unknown
May 11 10:37:07 username-desktop kernel: [ 6068.054239] hdg: status error: status=0x58 { DriveReady SeekComplete DataRequest }
May 11 10:37:07 username-desktop kernel: [ 6068.054243] ide: failed opcode was: unknown
May 11 10:37:07 username-desktop kernel: [ 6068.054283] hdg: status error: status=0x58 { DriveReady SeekComplete DataRequest }
May 11 10:37:07 username-desktop kernel: [ 6068.054287] ide: failed opcode was: unknown
May 11 10:37:07 username-desktop kernel: [ 6068.054336] hdg: status error: status=0x58 { DriveReady SeekComplete DataRequest }
May 11 10:37:07 username-desktop kernel: [ 6068.054340] ide: failed opcode was: unknown
May 11 10:37:07 username-desktop kernel: [ 6068.054383] hdg: status error: status=0x58 { DriveReady SeekComplete DataRequest }
May 11 10:37:07 username-desktop kernel: [ 6068.054389] ide: failed opcode was: unknown

I have searched with google for a solution using various search terms, some of which are listed below.

DBus error org.freedesktop.DBus.Error
Message did not receive a reply
Drive /dev/hdg does not contain audio files
does not contain audio files
ide: failed opcode was: unknown
hdg: status error: status=0x58
DriveReady SeekComplete DataRequest

I have searched for the exact quotes and for sites that just contain those words. I did find some sites with information pertaining to one or more of the error messages I am getting. I was not able to use what I found though because either I was not able to understand the post or it did not relate to my particular problem.

If anyone has a solution, or knows of a link to an easy to understand solution, I would greatly appreciate your assistance. 

If further information is needed, I will be happy to post it. At the moment I don´t know what else is needed.

---

### Post by sdennie on 2008-05-10
Do you have a scratched up CD in the CD drive?  I've gotten those messages when trying to read badly damaged CDs.

---

### Post by labinnsw on 2008-05-11
There was nothing in either drive

---

### Post by labinnsw on 2009-05-09
I replaced my hard Drive with a SATA hard drive freeing up the single IDE port for 2 DVD Drives as master and slave. The older hard drive is now on the RAID card for backups.

This setup has been running for months now without any errors.

Now if I can only figure out how to get XP to dual boot with Ubuntu on the same SATA hard disk. (It worked fine while I was using the IDE disk)

Before anyone asks, I use XP for my tax returns and since it is the OS used at work, I might as well remain familiar with it. More often than not I will go the virtual route, but very occasionally I will boot directly into XP.

---


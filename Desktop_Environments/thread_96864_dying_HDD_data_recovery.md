---
title: "dying HDD data recovery"
date: 2005-11-29
forum: Desktop Environments
---

### Post by Marc Higgins on 2005-11-29
Synopsis

Current version xubuntu locks up, (never seen that before from ubuntu) no term nothing, cant remember the state of the keyboard or HDD lights. 

Reboot, get through the boot menu, gets to "Uncompressing Linux.... OK booting the kernel loading please wait" then an error that reads something like HDA not read to receive data

Try another reboot no HDD detected. 

Reboot no HDD buy now the sounds coming from the HDD are like a CDrom starting (or a windup toy car) with sporadic clunks

Leave it sit for a minute, have a coffee & reboot once more the HDD is picked up by the bios this time & i have it a DSL disc (Damn Small Linux) in the CD drive & it boots it. 

Have mounted the homes partition, looks like i can see everything.

Now what is the best way to get a snap shot of the data off to somewhere safe ie off this box, can i do a dd if=/dev/hda3 of= ??? & scp this off somewhere

& is there anything fsck ish (all partitions are ext3) that I can run against the drive to try & repair the errors?

---

### Post by dcstar on 2005-11-29
[QUOTE=Marc Higgins]
......
Now what is the best way to get a snap shot of the data off to somewhere safe ie off this box, can i do a dd if=/dev/hda3 of= ??? & scp this off somewhere

& is there anything fsck ish (all partitions are ext3) that I can run against the drive to try & repair the errors?[/QUOTE]
Best thing would be to remove the crook drive, wrap it in a moisture proof bag, and put it in a freezer for about 30 minutes (this can temporarily "resurrect" a borderline failing HD).

Install your OS on a new HD, then take the bad one and try and use it by mounting it as a secondary drive.

Then if you can reliably get the data off it, do it before it fails totally!

---

### Post by Brent Dax on 2005-11-30
Whatever you do, **do not shut down the computer until you're finished recovering data or the drive has failed**.  That is by far the best way to move a drive from its deathbed to its coffin.

My suggestion:
1. Get any especially critical files off the disk first.  If you have another computer you can send them to, "scp" should work for this.
2. Image your partitions, most important ones first.  Try a command like this: "dd if=/dev/hda1 | gzip | ssh user@remote-box 'dd of=hda1.img.gz'".  This will stream the image across the network, so it never resides on local storage.

If the drive fails before you're finished rescuing data from it, the freezer trick does work for many people.

Errors like these are almost never recoverable--if you're seeing errors, then all of the drive's considerable efforts to repair itself, including using spare areas of the disk reserved to replace bad sectors, have already failed.  Tough luck, at least drives are cheap.

---

### Post by Marc Higgins on 2005-12-01
got the data it using dd over ssh thanks heaps!:D

lucky i didn't turn it off because the bios doesn't see the drive anymore, 

research the freezer thing & wow it works quite often. Drives that are over worked the read and write heads expand over time, once these expand so much they will not write to the platter. By putting it in the freezer it shrinks the heads back to an operable size & you get a chance to get the data off before they expand again.


Came across some really funny stuff while researching it; ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
i stuck my 3,5" Quantum lct 13 GB into the frigde, let it there for about 2 hrs, and when i took it back, it was 1,8"... so i could fit it in my laptop... gee, if i only knew this.... did i missed something ?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
I placed my hard disk in the oven and it got really hot, then I placed it in my pc plugged it in, melted the power connector and the whole thing short curcuited and blew my power supply. I am suing Compaq!
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

---


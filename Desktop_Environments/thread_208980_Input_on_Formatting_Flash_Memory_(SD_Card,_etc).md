---
title: "Input on Formatting Flash Memory (SD Card, etc)"
date: 2006-07-04
forum: Desktop Environments
---

### Post by dpaint4 on 2006-07-04
I've had absolutely no trouble at all formatting my USB Hard Drives, my Floppy Disks, or anything else there is to format. Ubuntu makes it all pretty easy. There's a utility for each of those things.

But I've had no luck finding on these forums, or by Googling, instructions or tools for formatting my SD Cards.

The latest Ubuntu supports my internal card reader, which Breezy didn't, so I'm thrilled about that, but most of the time (yet not always for some reason) it loads the card as read-only. Sometimes half-way through a session of transfers, the card suddenly 'becomes' read-only and little locks start appearing above all the files I'm dealing with.

If I eject the card and re-insert it, it no longer appears or mounts.

I respect this as something that Ubuntu has been working on and has made great progress towards.

My dream would be that by right-clicking on the card, like in Mac OS or Windows (or even Amiga for that matter), I could choose within the info dialog to format the card to whatever file system I liked. I wish this was possible with all media actually, but it's probably a tall order.

But absent that, does anyone know how to format a SD Card or flash memory in general from within Ubuntu?

My current strategy is to remove the card, insert it into my camera and format it!!! Silly isn't it? Plus then it won't be recognized again until the next time I start the computer.

I'd like something a little sleeker than that, if you've got any clues for me.

---

### Post by dpaint4 on 2006-07-05
Okay it's been 20 hours so I can bump this right? I'm trying to find information on how to format an SD Card. What utility should I use?

The Floppy and the Disk Manager both seem specialized to their specific media. I need to format SD cards, rather regularly to FAT32. What do you guys use for that?

---

### Post by reclusivemonkey on 2006-07-05
[QUOTE=dpaint4]Okay it's been 20 hours so I can bump this right? I'm trying to find information on how to format an SD Card. What utility should I use?

The Floppy and the Disk Manager both seem specialized to their specific media. I need to format SD cards, rather regularly to FAT32. What do you guys use for that?[/QUOTE]

I'm having some trouble with this myself, as Ubuntu seems to give me two icons for each Compact Flash or SD Card I put in my card reader. Gnome Partition Editor _should_ do what you want it to do, and looks pretty straightforward, but until you get a reply from someone who knows more I would hang on for a bit... unless SD card are particularly cheap where you are ;-)

---

### Post by kiddyfurby on 2006-07-13
I can format CF/MMC without problem, I have an USB card reader

System > administration > Disks

I have each card type shown up as different harddrive
disable access (umount) it and click format

---

### Post by Thindi on 2007-10-12
I have troubles formatting my SD cards, too. If I go to System/Administration, there is no Disk. So I have no idea how to format it. I use my camera too to do that. Another problem is, if I just delete files from the SD card, the used space remains the same. So if I delete some mp3s to be able to put new ones on, it's not possible because there is no room for it. I have to format the card completely and copy all the mp3s onto it again. Lots of time wasting there...

---

### Post by chipper_30 on 2007-10-19
I don't know about formating, but for the space problem after you deleted some files, it's because they're in the trash. If you empty the trash, you should get your free space again.

---

### Post by jlebrech on 2007-10-22
Easy, I just figured it out myself.

Insert your memory card,

open a terminal and type: df

df will tell you the device name of your memory card, in my case it was /dev/sdb1

unmount the disk

then just type: mkdosfs /dev/sdb1

mount it back (i just replugged it)

---

### Post by Thindi on 2007-12-03
Thanks a lot, Chipper!

---


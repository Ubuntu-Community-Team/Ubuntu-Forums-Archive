---
title: "MP3 player help"
date: 2005-12-14
forum: Desktop Environments
---

### Post by Oren on 2005-12-14
I have a USB MP3 player which Ubuntu recognises and allows me to swap files with.

However, I have a slight problem - 

Aftre a few loading and deleting of tracks, my MP3 player becomes confused.
 :eek: 

It starts scrambling bits of music which I already deleted, with track which are on the player (when you delete track from the player it creates a bin for the deleted items). I found that the best way to avoid this is by ocassionaly formatting the drive (has to be formatted to FAT). In windows this is not a problem. You just right click on the drive, choose format, and FAT and off you go!

How can I do this in Ubuntu? I tried through Gpart - delete the current patition (sdb) and then create a new FAT16 (I dont think Linux can do just FAT) partition with the maximum size possible (the size of the player - 256MB). But then I loose a big chunk of space for some reason.

Any suggestion will be greatly appreciated, Oren

---

### Post by Ampersand on 2005-12-14
Have you tried using the disks-admin utility (Sytem - Administration - Disks)? Select the mp3 player (probably sda1), disable it and you should be able to format it.

---

### Post by teaker1s on 2005-12-14
contact the manufacturer It sounds like the mp3 player has a firmware issue-there may be an update

---

### Post by Oren on 2005-12-14
[QUOTE=Ampersand]Have you tried using the disks-admin utility (Sytem - Administration - Disks)? Select the mp3 player (probably sda1), disable it and you should be able to format it.[/QUOTE]

If the MP3 Player is connected when I try to open 'Disks' - the disk manager tries to open but never quite gets there. Eventualy, I give up and just close it.
If I connect the player when 'Disk Manager' is already open, although the player is recognised and opened by Ubuntu, the 'Disk Manager' does not see it.

[QUOTE=teaker1s]contact the manufacturer It sounds like the mp3 player has a firmware issue-there may be an update[/QUOTE]

Unfortunately, this is an unnamed - non-branded palyer. One of them cheapo things. I already tried to google for any info about it and came back with zilch.
Is there a program which specializes in portable MP3 players?

---


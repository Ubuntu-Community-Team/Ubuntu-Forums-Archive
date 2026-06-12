---
title: "USB device trouble"
date: 2005-11-25
forum: Desktop Environments
---

### Post by ike on 2005-11-25
Hi,

I've run into some problems writing files to USB devices. I have a [USB flash drive]("http://images.tigerdirect.com/SKUimages/medium/K25-2520-main.jpg") that is automatically mounted when i plug it in, and that's just great. But if i copy files to it and unplug it, the files will disappear. But if i unmount the drive before unplugging, the files will be written to the drive correctly.

This morning i copied some .ogg-files to my flash memory based mp3-player (JOS MP-400) and unmounted the drive before unplugging. On my way to work i wanted to listen to the new songs, but they where not there!

This worked prefectly with hoary, and i believe it did work in breezy too until recently..

Does anyone else have the same problem? Is this one-of-many breezy issues? (there are still quite a few, you know.. FreeNX is a classic.)

---

### Post by ofek on 2005-11-25
Did you try to listen to .ogg files on that mp3 player before? 
Are you sure its comptibale with .ogg? (I know mine isn't)

---

### Post by kosmic on 2005-11-25
With USB Drives is always recomended that you umount the drive first, because linux writes the output to the cache and only saves to the Drive after you do Umount, if you do not umount the drive first it is probably that you will get an empty or corrupted files

---

### Post by ike on 2005-11-25
I just plugged in my mp3-player to my computer at work, and i noticed that 5 of the 13 files actually are on the drive, but they are all 0 bytes..

Maybe i unplugged it before the unmounting was finished.. If the files are copied after umount, like you say, it all make sense. Though it would be nice to have a progress bar or any kind of indication that work is being done ;)

It's strange that i've never had these problems before.. I never even had to unmount the USB drive, and i've used this mp3-player together with ubuntu for almost a year now.

And, yes ofek, it actually supports .ogg files. it's a neat little gadget ;)

---

### Post by Chris Tucker on 2005-11-25
wonder if anyone has modified the system to write the files when requested, not on unmount. i know it is possible, but i am wondering if anyone has done it.

---

### Post by ike on 2005-11-25
[QUOTE=Chris Tucker]wonder if anyone has modified the system to write the files when requested, not on unmount.[/QUOTE]

How do i do that? :)

---

### Post by kalin on 2005-11-25
You need the "sync" option of mount. It's hazardous to your flash though, read here for some explanation:

[Mount option hazardous to USB Flash!]("https://www.redhat.com/archives/fedora-list/2005-May/msg01859.html")

EDIT: in short "sync" causes the filesystem to not cache anything, which results in more writes to the flash. Flash memory has a limit though, and after too many writes it burns out. I would prefer unmounting it manually :)

---

### Post by ike on 2005-11-25
[QUOTE=kalin]EDIT: in short "sync" causes the filesystem to not cache anything, which results in more writes to the flash. Flash memory has a limit though, and after too many writes it burns out. I would prefer unmounting it manually :)[/QUOTE]

Good point. Is it possible that Ubuntu used the sync option earlier (i.e. in warty and hoary)?

---

### Post by kalin on 2005-11-25
[QUOTE=ike]Good point. Is it possible that Ubuntu used the sync option earlier (i.e. in warty and hoary)?[/QUOTE]

No idea :???:

---

### Post by Chris Tucker on 2005-11-25
[QUOTE=ike]How do i do that? :)[/QUOTE]
i dont know, i was asking.


as for the quote about USB FLASH and burnout.. i dont think its all media, and it takes a hell of a lot of writes.

---

### Post by kalin on 2005-11-25
[QUOTE=Chris Tucker]as for the quote about USB FLASH and burnout.. i dont think its all media, and it takes a hell of a lot of writes.[/QUOTE]

If I understand it correctly the problem is with the FAT filesystems, basically the file allocation table is being overwritten each time a new block of data is being allocated to a new file. Having the "sync" option on could lead to multiple overwrites of the same sector, storing the FAT table, for a single file copied.

It all depends on how the FAT table is being updated, the sector size (how much of a single file's allocation info is stored in one sector), the cluster size (size of the allocation blocks, basically how many blocks per file are needed), and the file size. I really don't have the exact numbers, but I would guess copying a 5MB mp3 file could lead to overwriting a single sector more than 100 times.

---


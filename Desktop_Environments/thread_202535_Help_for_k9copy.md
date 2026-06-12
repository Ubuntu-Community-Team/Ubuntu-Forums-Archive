---
title: "Help for k9copy"
date: 2006-06-23
forum: Desktop Environments
---

### Post by Kouya on 2006-06-23
I installed k9copy and tried to rip a dvd. I changed the dvd output directory to another drive (FAT32 partition) cos the partition which i install ubuntu in has less than 3 Gb left. However when i clicked the button to copy, k9copy could not work.

Hmm is it cos the output directory has to be the default one? or rather a directory that is not in another partition or drive?

---

### Post by Sgood1971 on 2006-06-23
Fat32 will not let you write a file over 4GB in size. That may be it, depending on the size of your DVD.

---

### Post by ubu-for on 2006-06-23
[QUOTE=Kouya]I changed the dvd output directory to another drive (FAT32 partition) ...[/QUOTE]

Linux can only read FAT partitions!

---

### Post by Kouya on 2006-06-23
oh so does that mean i should patition off some of my FAT32 and format that as FAT so i can tell k9copy to write my dvd copy there?

---

### Post by ubu-for on 2006-06-23
[QUOTE=Kouya]oh so does that mean i should patition off some of my FAT32 and format that as FAT so i can tell k9copy to write my dvd copy there?[/QUOTE]

No. You need a Linux partiton format! For example "Extended 3".

---

### Post by Kouya on 2006-06-23
oh rite! ok I'll go do it now... thanks so much!!!

---

### Post by stalker145 on 2006-06-23
[QUOTE=ubu-for]Linux can only read FAT partitions![/QUOTE]
ubu-for, I think you misspelled NTFS:p . Linux reads, writes, and can even do money laundering for FAT. It's the NTFS that it can only read reliably.

---


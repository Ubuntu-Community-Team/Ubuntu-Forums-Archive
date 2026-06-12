---
title: "Ubuntu and Vista not playing well"
date: 2009-03-05
forum: General Help
---

### Post by briarmoss on 2009-03-05
I recently reformatted my hard drive, and when i did so i created 2 20 GB NTFS partitions and one large ext3 partition. I installed ubuntu hardy 64-bit on the ext3, vista on the first ntfs, and left the second ntfs partition for music. I loaded all my music files onto the Music ntfs partition so i could sync rhythmbox in ubuntu (which works fine) and sync itunes in vista (which also worked fine). This was so i could sync my ipod with my music. The setup was working nicely until i edited my fstab to automount my Music partition in a certain place in my Ubuntu filesystem and used the command ntfslabel to rename my Music partition from "21.0 GB Media" to "Music". This works perfectly when i boot into Ubuntu, but when i boot into vista and try to access my drive (there it's called D:/) is gives me the error "D:/ is not accessible. The file or directory is corrupted and unreadable". I ran chkdsk on D: and everything ran perfectly and all the drive information was displayed (free space, partition size, number of files etc). Anyone have any clue how i can fix this?

---

### Post by wolfen69 on 2009-03-05
try renaming it back to "21.0 GB Media", and see what happens.

---

### Post by briarmoss on 2009-03-05
I think I'll just reformat the partition and try getting it to mount the way i want without it breaking before I transfer my music again. Thanks for the help though.

---

### Post by Slim Odds on 2009-03-05
> **wolfen69 said:**
> try renaming it back to "21.0 GB Media", and see what happens.

It wasn't "named" "21.0 GB Media". That's what Ubuntu calls things when they have no name (size will be whatever).

---

### Post by briarmoss on 2009-03-05
Slim Odds: Just for the record you're right. When I ran ntfslabel /dev/sda2 without any argument it gave me a blank line.

Also for the record: I reformatted the partition in ntfs with gparted (same as before) and went and used the same fstab line to mount it (after changing the uuid to the new one) and used ntfslabel to change the name to Music (just like before) and now Vista opens it up without any errors, so I really have no idea what happened. I guess it will remain a mystery unless something crops up, then I'll post.

---


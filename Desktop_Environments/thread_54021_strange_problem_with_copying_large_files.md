---
title: "strange problem with copying large files"
date: 2005-08-03
forum: Desktop Environments
---

### Post by aleahey on 2005-08-03
okay, i have a 120 gig hd mounted to /mnt/backup. when i copy a file to it, of greater size than 3 gigs, at exactly 3 gigs, it errors with a "cannot create file whateverfile, permission denied". i attempted it as root as well, just to see what would happen, and i get the same error.

dmesg | tail prints some gibberish about an I/O error and "DriveReady SeekComplete Error". judging by the dmesg, something errors and causes the drive to unmount, and a few seconds later remount itself.

any thoughts?

---

### Post by lol on 2005-08-03
what is the filesystem on your hd?

---

### Post by aleahey on 2005-08-03
ext3

---

### Post by lol on 2005-08-03
I had this kind of error with a defective HD, so maybe it would be a good idea to check yours for bad sectors. But if the drive is fine, I really don't have any clue, sorry.

---

### Post by aleahey on 2005-08-03
how would one check for bad sectors?

---

### Post by lol on 2005-08-04
[QUOTE=aleahey]how would one check for bad sectors?[/QUOTE]

with "badblocks". If you don't have it, apt-get e2fsprogs first (but I am sure it's installed by default).

Be careful though, the test CAN be destructive! I haven't used it since a long time, so I really don't remember which options you should use. Read the manpage before!

If the filesystem is empty and you don't mind formatting it again, you can also do the test with mkfs.ext3 -c

---


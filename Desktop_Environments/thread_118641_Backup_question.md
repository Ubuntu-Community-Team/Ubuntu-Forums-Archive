---
title: "Backup question"
date: 2006-01-17
forum: Desktop Environments
---

### Post by qferret on 2006-01-17
I generally have things working OK on my box now, but the file structure is full of garbage from hairbrained experiments of months past.

If I copy the root partition to a DVD, would I be able to copy it back onto a fresh install and have everything back to what it is now? I know this is not possible under Windows, but linux doesn't have a "registry"....

I am thinking of wiping the drive & starting over, rather than manually cleaning everything up. But if it proves to be a big PITA, or if I NEED something back up & running quickly, I'd like to be able to at least get it back to what it is today.

---

### Post by GeneralZod on 2006-01-17
I've done this several times in Knoppix by mounting the "/" partition (my /home and /var/cache/apt/archives are both on separate partitions to my "/" partition) and tar'ing up the contents.  I use bzip compression to get a smaller image (although it obviously takes significantly longer).  I then experimented, messed everything up, re-booted into knoppix, deleted the contents of my Ubuntu "/", and un-tar'd back over it.  I'm not sure if it's actually *recommended* as such, but it hasn't failed for me.  Yet :)

Note that I completely wipe my "/" before I restore my backed up .tar.bz2 file over it - I'm not sure how well it would work if you didn't wipe the partition first.

---

### Post by qferret on 2006-01-17
Perfect!

So worst case scenario is a boot into DSL and redo the / partition

Thanks

---

### Post by GeneralZod on 2006-01-17
[QUOTE=qferret]Perfect!

So worst case scenario is a boot into DSL and redo the / partition

Thanks[/QUOTE]

Well, worst case is that your data and computer explode in a shower of sparks and charred chips and set your dog on fire, but I've personally never seen that happen :) Do be careful, though - it's worked perfectly for me several times, but I may have simply gotten lucky.  I'd wait for a few more people to share their experiences before taking the plunge!

---

### Post by lamego on 2006-01-17
You can restore from a / as long your backup medium saves the correct ownership/permissions, this means you should probably use a disk image creation or a tar.
To restore from this image you will required some sysadmin expetise (to make sure you dont break the system during the restore).
I would recomment you to backup the / to a DVD and then making a fresh install.
If you need some files/folders just copy them the DVD later.

Also avoid repeating the mess, data files SHOULD be on /home to make sure to make a clean/backup on future system reinstalls.

---


---
title: "Breezy and Win2k Dual Boot -- Partition problems"
date: 2006-01-03
forum: General Help
---

### Post by Eulalia on 2006-01-03
Hello to you all!

This is the first time I post to this forum, cause it's the first time I have serious trouble with ubuntu.

About 1 year ago I created a dual boot system on my Laptop with Win2k (NFTS) on the first partition and Ubuntu (Warty Warthog)on the second (ext3)...plus FAT 32 partition for my data.
Everything worked perfectly!!!!

NOW I tried to create EXACTLY the same thing on my desktop (with Win2k and Breezy):

After installing Ubuntu and it's bootloader, Win2k wants to do a "consistency check" of the Ubuntu partition. Windows seems to be absolutely confused by the ext3 partition, and therefore gets very slow and instable.

WHY does Windows SEE the ext3 partition at all? (On my laptop system, the ext3 partition is invisible to Win2k and everything works perfectly!!!)

I think I made some mistake when formating the ext3 during ubuntu installation....

I there a possibility to hide the ext3 from Win2k?


:confused:

---

### Post by kenweill on 2006-01-03
Weird.

Never encountered that one. Windows seeing the ext3 partition.

---

### Post by Eulalia on 2006-01-03
Well, Win2k doesn't really SEE the ext3. (If it did, everything would be fine, I guess...)

Win detects a local HDD, but can't identify it. (...can't read, see it's size, etc.)

---

### Post by docmanny on 2006-01-03
You need to install a driver in Windows.

Try this:

[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)

---

### Post by kenweill on 2006-01-04
What did you do actually?

How many partitions do you have before you install Ubuntu?
How did you split the partition?

Sometimes, if you have an anti-virus installed in Windows, and you add new partition using partitioning tools, chances are that, the antivirus have a copy of the partition table. And when you next run, windows, it revert back the backup copy of the partition table(a record actually). I have experience this using Norton antivirus and AVG antivirus, before.

But I haven't experience the one you are experiencing right now.

Can you be more specific?

---

### Post by jonathanm on 2006-01-04
Try putting w2k on first and doing two partitions in fat32.  on the first put w2k and then partition the second when you install ubuntu into your boot, root, swap, etc
This also helps with the bootloader.

---


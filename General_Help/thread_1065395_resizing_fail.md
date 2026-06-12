---
title: "resizing fail"
date: 2009-02-09
forum: General Help
---

### Post by marshmallowfizz on 2009-02-09
here's the story, i ran out of space on my existing ubuntu partition so decided to resize it and make it bigger, i loaded up gparted from the live cd clicked resize, and it worked for about half an hour and told me it couldnt finish, that being said, im stuck with a 70g partition with 1 g of free space when i started out with a 30g partition, where did my 40 gigs go?

in short, 40gigs of space is being taken up by nothing after a resizing fail, any help would be greatly appreciated.     note: the free space was BEFORE the ubuntu partition on the table.

---

### Post by sedawk on 2009-02-09
I assume that partition is a ext3 partition !?

If there is any important data on that partition/hard disk/computer
make a backup of the partition or whole disk first (if not too late already!).

What you try (afterwards) is to boot the LiveCD and then
run a file system check on that partition.
You can use "-N" to see if there is anything that would be changed
before running the real "check+repair" mode.
Keep in that there is a risk of losing data when the partition
is repaired with fsck.

---


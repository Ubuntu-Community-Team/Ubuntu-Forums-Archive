---
title: "Is fragmentation a concern when deleting files from a NTFS"
date: 2009-02-22
forum: General Help
---

### Post by Dieseler on 2009-02-22
Is fragmentation a concern when deleting files from a NTFS formated disk within Ubuntu.
I'm not sure how Ubuntu deals with an old file system that was used by windows for file storage only.
I deleted a bunch of older junk from my ntfs Data disk last night from within Ubuntu and the thought occurred to me.
Should I defrag it with Windows?
Should I be concerned at all?

---

### Post by HermanAB on 2009-02-22
NTFS is actually quite good.  You don't need to defragment it.  Any perceived speed improvement tends to be imaginary if you do.

Cheers,

Herman

---

### Post by mb_webguy on 2009-02-22
Deleting a file on an ntfs partition in Ubuntu is no different than deleting a file on that partition in Windows, except that Ubuntu doesn't handle ntfs journaling, which has nothing to do with fragmentation.

The ntfs filesystem handles fragmentation better than FAT32, but nowhere near as well as native Linux filesystems like ext3.  If your ntfs filesystem gets about 80-90% of it's maximum capacity, you'll start getting more fragmentation, and you might want to consider defragging it in Windows.

---

### Post by Dieseler on 2009-02-23
Thanks for replies.
It is indeed beyond 90% full and thats why I was deleting and moving a bit of Data.
I will try to defrag it with Windows.

---

### Post by KeyserSoze93 on 2009-02-23
Suppose you (as I do) have a NTFS file system left over you your windows days, but don't have windows any more.

Is there anyway to defragment NTFS in Linux?

---

### Post by mb_webguy on 2009-02-23
Not that I know of, other than backing up all files on the partition, deleting the files on the partition (or reformatting it), and then restoring the backup.

And if you're going to do that, you might as well format it as ext3 while you're at it if you don't really have any need for ntfs.

---


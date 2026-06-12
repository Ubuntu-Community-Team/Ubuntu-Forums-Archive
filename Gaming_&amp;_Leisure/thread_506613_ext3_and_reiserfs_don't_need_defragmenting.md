---
title: "ext3 and reiserfs don't need defragmenting?"
date: 2007-07-21
forum: Gaming &amp; Leisure
---

### Post by benx009 on 2007-07-21
ext3 and reiserfs partitions don't need defragmenting like fat32 and ntfs, right?  can anyone enlighten me on why that is?

---

### Post by kostkon on 2007-07-21
I think most or all of the file systems that can be used under Linux really not need defragmenting. I heavily used an ext3 partition for 2 and more years and all I got was a mere 3% fragmentation of the file system. :)

---

### Post by benx009 on 2007-07-21
i read somewhere that the reason fragmentation doesn't happen on linux filesystems has something to do w/ the way data is stored on the hard disk.  windows stores a piece of data haphazardly thoughout the disk, while linux stores it all in one place.... or something like that....

---

### Post by Mblackwell on 2007-07-22
I think I've read that it continually manages the space when you access the disk as opposed to simply putting things in open spots. Basically it will keep rearranging the data into getting as much contiguous free space as possible at the end of the disk.

---

### Post by autocrosser on 2007-07-22
For more information take a look at:  [http://e2fsprogs.sourceforge.net/ext2intro.html](http://e2fsprogs.sourceforge.net/ext2intro.html)

---


---
title: "Copying to multiple disks simultaneously l"
date: 2009-05-29
forum: General Help
---

### Post by jbrown96 on 2009-05-29
I'm in the middle of backing up a lot of data, but I need some help on doing the last stage. 
I'll explain the whole process so you can understand. 
1) ~33GB is transferring to an external hard drive (USB) right now.
2) On a HTPC, I have two 1TB drivers that need to be rsync'd together (they probably have about 10-15GB different)
3) The ~33GB from the external will then need to be copied to BOTH 1TB drives.

I know how to do 1 and 2, and I can do them at the same time, so it saves a lot of time. However, is there a way to do #3 at the same time. Could I use cp with two destinations, so the data on the external is only read once? Some sort of read-once, write-twice option?? Or maybe with rsync?

Here are my mount locations:
/media/backup   (backup 1TB)
/media/library  (my media collection, 1TB)
/media/external (USB external 250GB)

Thanks for the help

---


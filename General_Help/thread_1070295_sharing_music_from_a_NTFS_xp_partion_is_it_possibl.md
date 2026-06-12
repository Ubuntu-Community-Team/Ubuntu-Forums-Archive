---
title: "sharing music from a NTFS xp partion? is it possible?"
date: 2009-02-15
forum: General Help
---

### Post by JDMB20TDA on 2009-02-15
I was running ubuntu, ran into so many problems I reinstalled windows and will soon be Dual booting.
I have all my music and pictures that I had backed up on 2 separate drives.
I copied it all to my main boot drive and my question is.
 
Could I access the music and pictures in Ubuntu and XP or if they are stored in the windows partion are they inaccessible through Ubuntu?

---

### Post by -kg- on 2009-02-15
Yes, you can access your files on an ntfs drive with Ubuntu easily.  You might have to do a little tweaking of your fstab file (which is not a problem at all...if you have problems, just post here or do a search, it isn't the first time) depending on your installation, but once done you will have full read and write capabilities to such a partition without problem.

As matter of fact, I access my music and other files from an ntfs partition on both my desktop and laptops.  I have them on an external drive, on which my music partition is formatted to ntfs, and I switch between them depending on what computer I'm working on.

---

### Post by JDMB20TDA on 2009-02-15
that was very helpful thank you very much.
I knew I was able to mount and access but wasnt sure if they were partioned separately if that would make a difference.

---

### Post by mb_webguy on 2009-02-15
One of the nice things about Linux is that it really doesn't matter how many partitions you have, once they're mounted it's all one filesystem.  Unlike Windows, where each partition must have a separate drive letter, in Linux any directory can be mounted on a separate partition, and any partition can be mounted anywhere in your filesystem.

---


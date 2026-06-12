---
title: "Partitioning (resize) and other nightmares"
date: 2005-09-07
forum: Desktop Environments
---

### Post by duminas on 2005-09-07
First and foremost, I apologize for how rant-esque this will sound, but Ubuntu is *really* beginning to irk me beyond compare..

The problem?

Oh, nothing. Aside from the fact that **I can't resize Ubuntu's partition without it freaking out and forcing me to _completely_ reinstall the OS!** This is with ext2, ext3, and reiserfs that it all does this.

With ext2 and ext3, I get a lot of output I care not to try to scribe down, since when it happens my install BREAKS, and then "All is not well!" With reiser, it just crashes. I am using *parted* from an Ubuntu LiveCD to do resizing.

My table is setup as such:```
Disk geometry for /dev/hda: 0.000-76319.085 megabytes
Disk label type: msdos
Minor    Start       End     Type      Filesystem  Flags
1          0.031   5718.449  primary   ext3        boot
2       5718.450  76316.594  extended
5       5718.480   6204.792  logical   linux-swap
7       6204.823  10974.089  logical   ext3
6      10974.120  76316.594  logical   ext3
```Now, 1 is /, 5 is swap, 6 is /home, and 7 is data storage (/umedia). What I am trying to do is this:
```
Setup Wanted:
1           3.7 GB               / (Ubuntu)
2           2.0 GB               / (Gentoo -- Let's have Ubuntu ignore this.)
3 or 4     EXTENDED
#           5.0 GB               /home (Ubuntu)
#           68.5 GB              /umedia (Both)
```Can I do this within Linux without breaking things terribly? I want to change the extended to be a MINOR of 3 or higher if I can (and if having 1, 2, 4, 5, 6 won't break things). I **_MUST_** keep the data in the 68.5 GB partition at all costs! Burning to DVDs is not a viable option at this time. (Windows could resize my partitions (even the Linux ones) perfectly well, so why does Linux keep breaking itself irreprably when I try to resize?)

Thanks for your time.

---

### Post by frodon on 2005-09-07
It's just an idea but if you have enough free space you could [backup](http://ubuntuforums.org/showthread.php?t=35087)  your ubuntu partition on another drive then resize your partition and then restore your ubuntu partition on the new resized partition.

---

### Post by duminas on 2005-09-07
It's a good idea, and I have space for it.
However, after I do this resizing, I am for some reason incapable of performing operations on the drive.

Such that trying to *mount* it will result in an error like "Operation not permitted", and this is with root rights.

---


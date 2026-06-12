---
title: "Ubuntu copy-paste hidden files and convert them in none-hidden files. Why? Help!"
date: 2009-07-08
forum: Desktop Environments
---

### Post by InterlinkKnight on 2009-07-08
Hi. I’m relative a beginner with Ubuntu but I’ve been using Ubuntu for a while and it seems that when I copy-paste a hidden file or folder, Ubuntu convert the paste files or folders in regular files (none hidden).

I search for this and don’t find any way to avoid this.

Is there any settings that can change this? I just want to Ubuntu paste hidden files as it was in the original file (hidden too).

Help me guys. Thanks

---

### Post by Ugluk on 2009-07-08
What Ubuntu release do you use? Also note, that hidden state is not preserved on NTFS or FAT volumes due to driver deficiency.

---

### Post by InterlinkKnight on 2009-07-08
> **Ugluk said:**
> What Ubuntu release do you use? Also note, that hidden state is not preserved on NTFS or FAT volumes due to driver deficiency.

My version is 8.04.1

I don't understand very well. Hidden state is not preserved on NTFS or FAT volumes due to driver deficiency?

I can’t solve this because I don’t get the right drivers for my hard drive?

My hard drive is formatted in NTFS.

What I need to do? Or it can be solved?

---

### Post by lykwydchykyn on 2009-07-08
Are you copying and pasting from an NTFS drive to an NTFS drive, or from an NTFS drive to some other kind of drive, or from a Linux (EXT3/EXT4/Reiserfs/etc) partition to NTFS?

Attributes like "hidden" are part of the filesystem, they aren't usually preserved when you move them from one filesystem type to another.  Most filesystems used on Linux don't use a "hidden" attribute, you just prepend the name with a dot to hide the files.

---

### Post by InterlinkKnight on 2009-07-08
> **lykwydchykyn said:**
> Are you copying and pasting from an NTFS drive to an NTFS drive, or from an NTFS drive to some other kind of drive, or from a Linux (EXT3/EXT4/Reiserfs/etc) partition to NTFS?

Attributes like "hidden" are part of the filesystem, they aren't usually preserved when you move them from one filesystem type to another.  Most filesystems used on Linux don't use a "hidden" attribute, you just prepend the name with a dot to hide the files.

I’m copying and pasting from an NTFS drive to an NTFS drive (the same drive and partition).

This sucks.

Thanks you guys very much. I will not use Ubuntu for these kinds of operations.

I just wan’t to be sure it doesn’t have solution.

---

### Post by Ugluk on 2009-07-08
You may contact [ntfs-3g driver developers]("http://forum.ntfs-3g.org/"), and hope that they will implement this feature in several next years; by the way, messing with NTFS files under Ubuntu will reset all the permissions you may have set for these files, so beware...

---


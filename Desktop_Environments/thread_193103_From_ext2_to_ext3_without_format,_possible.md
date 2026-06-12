---
title: "From ext2 to ext3 without format, possible?"
date: 2006-06-09
forum: Desktop Environments
---

### Post by Orta on 2006-06-09
Well, the subject pretty much sums my question. I had my partition formatted as ext2 (from old distros) and didn't even noticed/cared about that while installing Dapper 6.06. Is it possible to use the more recent filesystem without formatting/reinstalling? Many thanks.

---

### Post by Rackerz on 2006-06-09
I don't think there is :(.

---

### Post by Orta on 2006-06-09
Well, I googled [this website]("http://www.troubleshooters.com/linux/ext2toext3.htm") but I wonder if it works with Ubuntu...

---

### Post by mannheim on 2006-06-09
From the man page of tune2fs, comes this information:

```
 
        -j    Add  an ext3 journal to the filesystem.  If the -J option is not
              specified, the default journal parameters will be used to create
              an  appropriately  sized journal (given the size of the filesys&#8208;
              tem) stored within the filesystem.  Note that you must be  using
              a kernel which has ext3 support in order to actually make use of
              the journal.

              If this option is used to create a journal on a mounted filesys&#8208;
              tem,  an  immutable  file, .journal, will be created in the top-
              level directory of the filesystem, as it is the only safe way to
              create the journal inode while the filesystem is mounted.  While
              the ext3 journal is visible, it is not safe  to  delete  it,  or
              modify  it  while the filesystem is mounted; for this reason the
              file is marked immutable.  While checking unmounted filesystems,
              e2fsck(8)  will automatically move .journal files to the invisi&#8208;
              ble, reserved journal inode.  For all filesystems except for the
              root filesystem,  this should happen automatically and naturally
              during the next reboot cycle.   Since  the  root  filesystem  is
              mounted read-only, e2fsck(8) must be run from a rescue floppy in
              order to effect this transition.

              [COLOR="Red"]On some distributions, such as Debian, if an initial ramdisk  is
              used, the initrd scripts will automatically convert an ext2 root
              filesystem to ext3 if the /etc/fstab  file  specifies  the  ext3
              filesystem  for  the root filesystem in order to avoid requiring
              the use of a rescue floppy to add an ext3 journal  to  the  root
              filesystem.[/COLOR]


```

This suggests that you need only edit your /etc/fstab file. If the fstab file contains a line like:

```
/dev/hda1   /   ext2    defaults,errors=remount-ro 0       1

```

then you could change "ext2" to "ext3", and the filesystem will be converted at the next boot.

---

### Post by Orta on 2006-06-09
That worked nicely, thanks!

---

### Post by nate_nightroad on 2007-06-06
hey,i found tis page and i'm interested in converting my ext2 to ext3 without formating it....i tried to change ext2 to ext3 at the fstab but it did not work....

using 7.04 64 by the way

any idea fellas?

---

### Post by mcduck on 2007-06-06
> **nate_nightroad said:**
> hey,i found tis page and i'm interested in converting my ext2 to ext3 without formating it....i tried to change ext2 to ext3 at the fstab but it did not work....

using 7.04 64 by the way

any idea fellas?
just use the tune2fs command mannheim gave on the 2nd post.

Ext3 is just ext2 with added journaling, creating the journal will convert it into ext3.

---

### Post by JowCG on 2008-07-20
```
# tune2fs -j /dev/hdx
```

Where / dev / hdx should be replaced by the partition being converted, of course.

You can also change the intervals that the file system should be checked by fsck disabling this check, because that is no longer so important because the greater security of ext3. This can be done as follows:

```
tune2fs -i 0 -c 0 /dev/hdx
```
	
Now it's just restart the computer that you are with your new file system working. Use the dmesg command to check that the boot will appear on messages about mounting the file system as ext3.

---


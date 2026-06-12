---
title: "ext3 to ext4 ?"
date: 2009-04-02
forum: General Help
---

### Post by anjanesh on 2009-04-02
If I upgrade from 8.10 to 9.04, can I change all my file-systems from ext3 to ext4 ?

---

### Post by ptn107 on 2009-04-02
"It is possible to mount both ext3 (and ext2, in kernels 2.6.28 and later) filesystems directly using the ext4 filesystem driver. This will allow you to use many of the in-core performance enhancements such as delayed allocation (delalloc) and multi-block allocation (mballoc), and large inodes if your ext3 filesystem have been formatted with large inodes as is the default with newer versions of e2fsprogs. **_Simply mounting an ext3 (or ext2) filesystem with a modern (2.6.27+) version of ext4 will not change the on-disk structures_**, and it is possible to revert to the ext3 (or ext2) driver should there be any problem with ext4.

In addition to the in-core performance enhancements, there are additional features which modify the on-disk format from what ext3 understands, such as extents, which can significantly improve the ext4 filesystem performance, but mean the filesystem cannot be mounted by kernels that do not support ext4. There are additional ext4 features, such as flex_bg and > 16TB filesystem support that can only be enabled at format time via mke2fs." [1]

You *could* just tell fstab to mount ext3 to ext4 if you wanted to, but if you want to take advantage of the better things (eg. extents) backup your data and reformat ext4.

[1] [http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4](http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4)

---

### Post by HermanAB on 2009-04-02
I would give Ext4 another year to mature before I would even try it.  It may also be a good idea to use a UPS with Ext4 since some people have had corruptions.

---

### Post by lensman3 on 2009-04-02
I've been running ext4 on a drive I use for backups only.  It was formatted first with "truecrypt"  then the file system was placed on top of truecrypt.  If the drive is stolen then the drive will look like random noise.  The truecrypt pass phrases have to be applied first before the drive can be mounted.

It has been formatted ext4 for about 4 months.  So far no trouble.  I think ext4 is ready for "prime time".  I'm about to convert another ext3 partition to ext4, but haven't had the time.

I'm not sure that ext4 formatting is available yet for a new install.  I think ext4 has to be applied after the fact.

---


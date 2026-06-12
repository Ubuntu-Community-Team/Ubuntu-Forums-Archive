---
title: "Ubuntu Beats Windows 7 and Windows XP by a Huge Margin"
date: 2009-07-08
forum: Desktop Environments
---

### Post by ocsid80 on 2009-07-08
A series of file system performance tests prove that Ubuntu beats
Windows 7 and Windows XP in all file management operations including 
file search, file classification, storage analysis, file copy and file synchronization.

According to a file systems performance comparison published here:

[http://www.flexense.com/resources/file_systems_performance_comparison.html](http://www.flexense.com/resources/file_systems_performance_comparison.html)

The brand new Windows 7 is actually slower than the 8-years-old Windows XP
in all tests and Ubuntu 9.04 leads both Windows versions in all file management
operations by a huge margin.

---

### Post by Fzang on 2009-07-08
Unfortunately, it's not the benchmarks that count, but the user experience.

---

### Post by ocsid80 on 2009-07-08
In fact, there was no intention to publish any performance comparisons.

During the last month, while we were finishing porting FlexTk to Ubuntu,
we have discovered that almost all operations with large amounts of files
are actually performing much faster on Ubuntu.

These are not just benchmarks and it's all about how much time you need
to wait for an operation to complete.

If someone needs to search through, or perform a storage utilization analysis
on a disk or storage system, or synchronize files between two disks with a few
hundreds of files it will be significantly faster on Ubuntu.

---

### Post by Petrik_CZ on 2009-07-08
Considering, that ext4 is about 20% faster than ext3 in many applications, I wonder how would this benchmark looked with ext4 in ubuntu :)

---

### Post by ocsid80 on 2009-07-08
We are preparing for two additional benchmarking sessions - 
the first one that will compare a number of file systems such
as EXT3, EXT4  and XFS under Linux x64 and the second one
comparing a Linux NAS server with a Windows NAS server
over Gigabit network.

Could anyone tell if there are other file systems (in addition to
EXT3, EXT4  and XFS) worth considering for the benchmark?

---

### Post by choman on 2009-07-08
Be nice see this compare lots of filsystems
  - solaris 10 w/ zfs
  - linux w/ zfs (if this ever happens)
  - brtfs
  - nilfs2

One could also add the performance hit with FUSE, which then would 
allow zfs under linux

The NAS should test ext3, ext4 in RAID 0, 1, 5, 6 at a minimum.
however, one could argue for the other variants: 0+1, 1+0,  etc

This obviously leads into JBOD and LVM as well.

Well enough for know, just my 16 cents

---


---
title: "rsync between ext3 and ntfs question"
date: 2009-01-29
forum: General Help
---

### Post by dcymbal on 2009-01-29
Hi,

I'm using Ubuntu 8.10 with 2.6.27.11 i686 kernel and rsync 3.0.3.  I have 2 external USB2 HDD for backups.  One external drive is ext3 and one is ntfs.  Source system is ext3.

I have noticed some differences in behavior when backing up from ext3 to the ntfs drive which I have not seen discussed.  As a simple test I created a new local ext3 and ntfs partition and see the same behavior.  That is, even when the ntfs backup is completely up to date, rsync correctly does not recopy any data, but rsync (with -v verbose set) prints out every single directory in the hierarchy as it scans for differences.  It does not behave this way when the target is ext3.  Originally I chalked up the speed difference to performance differences between ext3 and ntfs, but with this difference in output behavior I am wondering if there is not some additional optimization that is taking place for ext3 not available to nfs.  Any ideas?  The following is the output I get for the two backups.  It is consistently reproducible.

$sudo rsync -av --exclude=.gvfs . /tmp/ext3/
sending incremental file list

sent 4420 bytes  received 23 bytes  8886.00 bytes/sec
total size is 2879586  speedup is 648.12

$ sudo rsync -av --exclude=.gvfs . /tmp/ntfs/
sending incremental file list
./
doc/
lib/
packaging/
packaging/bin/
packaging/lsb/
packaging/solaris/
popt/
support/
testhelp/
testsuite/
zlib/

sent 5074 bytes  received 677 bytes  11502.00 bytes/sec
total size is 2879586  speedup is 500.71

mount output:
/dev/sdb2 on /tmp/ntfs type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

/dev/sdb3 on /tmp/ext3 type ext3 (rw)

---


---
title: "Unable to Mount External Hard Drive -- data exists but isn't readable?"
date: 2009-06-12
forum: General Help
---

### Post by shmi85 on 2009-06-12
Hi all:

I'm running ubuntu 9.04 on an IBM Thinkpad R52. I have a 200gig external hard drive by I/O Magic which is about a year and a half old. I haven't ever had any problems with it like this before.

Earlier today, I opened it and the window displayed 0 items. The status bar at the bottom says only 83gigs are available, so I think all my data is still there, the file system isn't working correctly. After a reboot of the external drive and my laptop, the first two levels of folders appeared in the file browser, but all the folders say they have "0 items" and they do indeed look empty.

When I try and unmount and remount, I get an error saying the drive cannot be unmounted, but then it unmounts anyway. When I try and mount it again, I get this error:

Cannot mount volume.
Unable to mount the volume 'franz'.
Details
mount:wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or helper program, or other error   In some cases useful info is found in syslog -- try dmesg | tail or so

And it genuinely will not mount again. So I run the suggested command and this is what I got:

emg@trotsky:~$ dmesg | tail
[ 5047.048995] EXT2-fs error (device sdb1): ext2_readdir: bad page in #11141220
[ 5047.049806] EXT2-fs error (device sdb1): ext2_readdir: bad page in #14385165
[ 5047.050555] EXT2-fs error (device sdb1): ext2_readdir: bad page in #17678337
[ 5047.051304] EXT2-fs error (device sdb1): ext2_readdir: bad page in #22462465
[ 5073.990819] EXT2-fs error (device sdb1): ext2_readdir: bad page in #103
[ 5151.445453] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 5151.445465] sd 6:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 5151.445475] sd 6:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 5151.445485] end_request: I/O error, dev sdb, sector 71
[ 5151.445513] EXT2-fs: unable to read group descriptors
emg@trotsky:~$ 


I have no idea what's going on or how to fix it. But I'd really appreciate any trouble-shooting, since I have a lot of backed up work and media on my drive and I'm going to be royally screwed without it.

Thanks in advance!

~Elisa

---

### Post by shmi85 on 2009-06-12
I'm reposting this here because I think I picked the wrong support category for it.

Hi all:

I'm running ubuntu 9.04 on an IBM Thinkpad R52. I have a 200gig external hard drive by I/O Magic which is about a year and a half old. I haven't ever had any problems with it like this before.

Earlier today, I opened it and the window displayed 0 items. The status bar at the bottom says only 83gigs are available, so I think all my data is still there, the file system isn't working correctly. After a reboot of the external drive and my laptop, the first two levels of folders appeared in the file browser, but all the folders say they have "0 items" and they do indeed look empty.

When I try and unmount and remount, I get an error saying the drive cannot be unmounted, but then it unmounts anyway. When I try and mount it again, I get this error:

Cannot mount volume.
Unable to mount the volume 'franz'.
Details
mount:wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or helper program, or other error In some cases useful info is found in syslog -- try dmesg | tail or so

And it genuinely will not mount again. So I run the suggested command and this is what I got:

emg@trotsky:~$ dmesg | tail
[ 5047.048995] EXT2-fs error (device sdb1): ext2_readdir: bad page in #11141220
[ 5047.049806] EXT2-fs error (device sdb1): ext2_readdir: bad page in #14385165
[ 5047.050555] EXT2-fs error (device sdb1): ext2_readdir: bad page in #17678337
[ 5047.051304] EXT2-fs error (device sdb1): ext2_readdir: bad page in #22462465
[ 5073.990819] EXT2-fs error (device sdb1): ext2_readdir: bad page in #103
[ 5151.445453] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 5151.445465] sd 6:0:0:0: [sdb] Sense Key : Medium Error [current]
[ 5151.445475] sd 6:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 5151.445485] end_request: I/O error, dev sdb, sector 71
[ 5151.445513] EXT2-fs: unable to read group descriptors
emg@trotsky:~$


I have no idea what's going on or how to fix it. But I'd really appreciate any trouble-shooting, since I have a lot of backed up work and media on my drive and I'm going to be royally screwed without it.

Thanks in advance!

~Elisa

---

### Post by shmi85 on 2009-06-12
bumpity bump.

---

### Post by merlinus on 2009-06-12
TestDisk should allow you to access the files.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---


---
title: "ipod mounting problems"
date: 2006-02-17
forum: Desktop Environments
---

### Post by kenailes on 2006-02-17
could someone please look at my dmesg log and tell me why my ipod won't mount?  Thanks in advance

[4296334.498000]   Vendor: Apple     Model: iPod              Rev: 1.62
[4296334.498000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4296334.506000] usb-storage: device scan complete
[4296334.615000] SCSI device sda: 58605120 512-byte hdwr sectors (30006 MB)
[4296334.616000] sda: Write Protect is off
[4296334.616000] sda: Mode Sense: 6c 00 00 08
[4296334.616000] sda: assuming drive cache: write through
[4296334.620000] SCSI device sda: 58605120 512-byte hdwr sectors (30006 MB)
[4296334.621000] sda: Write Protect is off
[4296334.621000] sda: Mode Sense: 6c 00 00 08
[4296334.621000] sda: assuming drive cache: write through
[4296334.621000]  /dev/scsi/host0/bus0/target0/lun0: p1 p2
[4296334.640000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
[4296373.492000] FAT: Unrecognized mount option "gid=autofs" or missing value
[4296374.060000] UDF-fs: No partition found (1)
[4296374.208000] UDF-fs: No partition found (1)
[4296374.319000] Unable to identify CD-ROM format.
[4296374.375000] Unable to identify CD-ROM format.
[4296374.380000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4296374.381000] FAT: bogus logical sector size 2
[4296374.381000] VFS: Can't find a valid FAT filesystem on dev sda.
[4296374.386000] FAT: bogus logical sector size 2
[4296374.386000] VFS: Can't find a valid FAT filesystem on dev sda.
[4296374.393000] NTFS-fs warning (device sda): parse_options(): Option iocharset is deprecated. Please use option nls=<charsetname> in the future.
[4296374.394000] NTFS-fs error (device sda): read_ntfs_boot_sector(): Primary boot sector is invalid.
[4296374.394000] NTFS-fs error (device sda): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[4296374.394000] NTFS-fs error (device sda): ntfs_fill_super(): Not an NTFS volume.
[4296374.400000] NTFS-fs error (device sda): read_ntfs_boot_sector(): Primary boot sector is invalid.
[4296374.400000] NTFS-fs error (device sda): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[4296374.400000] NTFS-fs error (device sda): ntfs_fill_super(): Not an NTFS volume.
[4296374.419000] HFS+-fs: unable to find HFS+ superblock
[4296374.426000] HFS+-fs: unable to find HFS+ superblock
[4296374.446000] VFS: Can't find a HFS filesystem on dev sda.
[4296374.451000] VFS: Can't find a HFS filesystem on dev sda.
[4296374.457000] VFS: Can't find ext3 filesystem on dev sda.
[4296374.462000] VFS: Can't find ext3 filesystem on dev sda.
[4296374.468000] VFS: Can't find an ext2 filesystem on dev sda.
[4296374.473000] VFS: Can't find an ext2 filesystem on dev sda.
[4296374.497000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
[4296374.504000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
[4296374.549000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[4296374.550000] SGI XFS Quota Management subsystem
[4296374.555000] XFS: bad magic number
[4296374.555000] XFS: SB validate failed
[4296374.561000] XFS: bad magic number
[4296374.561000] XFS: SB validate failed
[4296374.576000] JFS: nTxBlock = 3905, nTxLock = 31245
[4296377.069000] FAT: Unrecognized mount option "gid=autofs" or missing value
[4296377.078000] FAT: Unrecognized mount option "gid=autofs" or missing value
[4296377.085000] FAT: Unrecognized mount option "gid=autofs" or missing value

---


---
title: "Kubuntu 5.10 tries to automount sda1 *and* sda"
date: 2005-12-02
forum: Desktop Environments
---

### Post by reagle on 2005-12-02
Unlike most problems where folks have trouble with the automount, I have too much of a good thing. I have an external single primary partition ext3 formatted usb drive. (At one point I had formatted it without a partition even (just the whole disk) and perhaps that confused it?) Can I tell automount not to worry about /dev/sda and just focus on /dev/sda1?

Dec  2 13:59:51 localhost kernel: [4298871.006000] usb 4-2: new high speed USB device using ehci_hcd and address 8
Dec  2 13:59:51 localhost kernel: [4298871.083000] scsi5 : SCSI emulation for USB Mass Storage devices
Dec  2 13:59:51 localhost kernel: [4298871.084000] usb-storage: device found at 8
Dec  2 13:59:51 localhost kernel: [4298871.084000] usb-storage: waiting for device to settle before scanning
Dec  2 13:59:51 localhost usb.agent[14078]:      usb-storage: already loaded
Dec  2 13:59:56 localhost kernel: [4298876.084000]   Vendor: WDC       Model: WD1200JB-32EVA0   Rev: 15.0
Dec  2 13:59:56 localhost kernel: [4298876.084000]   Type:   Direct-Access                      ANSI SCSI revision: 02
Dec  2 13:59:56 localhost kernel: [4298876.087000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
Dec  2 13:59:56 localhost kernel: [4298876.087000] sda: assuming drive cache: write through
Dec  2 13:59:56 localhost kernel: [4298876.090000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
Dec  2 13:59:56 localhost kernel: [4298876.090000] sda: assuming drive cache: write through
Dec  2 13:59:56 localhost kernel: [4298876.090000]  /dev/scsi/host5/bus0/target0/lun0: p1
Dec  2 13:59:56 localhost kernel: [4298876.095000] Attached scsi disk sda at scsi5, channel 0, id 0, lun 0
Dec  2 13:59:56 localhost kernel: [4298876.096000] usb-storage: device scan complete
Dec  2 13:59:56 localhost scsi.agent[14126]:      sd_mod: loaded sucessfully (for disk)
Dec  2 13:59:57 localhost usbmount[14206]: cannnot execute /sbin/udev_volume_id
Dec  2 13:59:59 localhost kernel: [4298879.424000] UDF-fs: No VRS found
Dec  2 13:59:59 localhost kernel: [4298879.429000] UDF-fs: No VRS found
Dec  2 14:00:00 localhost kernel: [4298879.521000] Unable to identify CD-ROM format.
Dec  2 14:00:00 localhost kernel: [4298879.566000] Unable to identify CD-ROM format.
Dec  2 14:00:00 localhost kernel: [4298879.568000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
Dec  2 14:00:00 localhost kernel: [4298879.570000] FAT: bogus number of reserved sectors
Dec  2 14:00:00 localhost kernel: [4298879.570000] VFS: Can't find a valid FAT filesystem on dev sda1.
Dec  2 14:00:00 localhost kernel: [4298879.573000] FAT: bogus number of reserved sectors
Dec  2 14:00:00 localhost kernel: [4298879.573000] VFS: Can't find a valid FAT filesystem on dev sda1.
Dec  2 14:00:00 localhost kernel: [4298879.575000] NTFS-fs warning (device sda1): parse_options(): Option iocharset is deprecated. Please use option nls=<charsetname> in the future.
Dec  2 14:00:00 localhost kernel: [4298879.575000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
Dec  2 14:00:00 localhost kernel: [4298879.575000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
Dec  2 14:00:00 localhost kernel: [4298879.575000] NTFS-fs error (device sda1): ntfs_fill_super(): Not an NTFS volume.
Dec  2 14:00:00 localhost kernel: [4298879.578000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
Dec  2 14:00:00 localhost kernel: [4298879.578000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
Dec  2 14:00:00 localhost kernel: [4298879.578000] NTFS-fs error (device sda1): ntfs_fill_super(): Not an NTFS volume.
Dec  2 14:00:00 localhost kernel: [4298879.581000] HFS+-fs: unable to find HFS+ superblock
Dec  2 14:00:00 localhost kernel: [4298879.584000] HFS+-fs: unable to find HFS+ superblock
Dec  2 14:00:00 localhost kernel: [4298879.587000] VFS: Can't find a HFS filesystem on dev sda1.
Dec  2 14:00:00 localhost kernel: [4298879.590000] VFS: Can't find a HFS filesystem on dev sda1.
Dec  2 14:00:00 localhost kernel: [4298879.622000] kjournald starting.  Commit interval 5 seconds
Dec  2 14:00:00 localhost kernel: [4298879.624000] EXT3 FS on sda1, internal journal
Dec  2 14:00:00 localhost kernel: [4298879.624000] EXT3-fs: mounted filesystem with ordered data mode.
Dec  2 14:00:00 localhost kernel: [4298880.103000] UDF-fs: No partition found (1)
Dec  2 14:00:00 localhost kernel: [4298880.105000] UDF-fs: No partition found (1)
Dec  2 14:00:00 localhost kernel: [4298880.149000] Unable to identify CD-ROM format.
Dec  2 14:00:00 localhost kernel: [4298880.152000] Unable to identify CD-ROM format.
Dec  2 14:00:00 localhost kernel: [4298880.154000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
Dec  2 14:00:00 localhost kernel: [4298880.161000] FAT: bogus number of reserved sectors
Dec  2 14:00:00 localhost kernel: [4298880.161000] VFS: Can't find a valid FAT filesystem on dev sda.
Dec  2 14:00:00 localhost kernel: [4298880.164000] FAT: bogus number of reserved sectors
Dec  2 14:00:00 localhost kernel: [4298880.164000] VFS: Can't find a valid FAT filesystem on dev sda.
Dec  2 14:00:00 localhost kernel: [4298880.166000] NTFS-fs warning (device sda): parse_options(): Option iocharset is deprecated. Please use option nls=<charsetname> in the future.
Dec  2 14:00:00 localhost kernel: [4298880.166000] NTFS-fs error (device sda): read_ntfs_boot_sector(): Primary boot sector is invalid.
Dec  2 14:00:00 localhost kernel: [4298880.166000] NTFS-fs error (device sda): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
Dec  2 14:00:00 localhost kernel: [4298880.195000] HFS+-fs: unable to find HFS+ superblock
Dec  2 14:00:00 localhost kernel: [4298880.197000] HFS+-fs: unable to find HFS+ superblock
Dec  2 14:00:00 localhost kernel: [4298880.201000] VFS: Can't find a HFS filesystem on dev sda.
Dec  2 14:00:00 localhost kernel: [4298880.204000] VFS: Can't find a HFS filesystem on dev sda.
Dec  2 14:00:00 localhost kernel: [4298880.211000] EXT3-fs error (device sda): ext3_check_descriptors: Block bitmap for group 880 not in group (block 0)!
Dec  2 14:00:00 localhost kernel: [4298880.212000] EXT3-fs: group descriptors corrupted !
Dec  2 14:00:00 localhost kernel: [4298880.219000] EXT3-fs error (device sda): ext3_check_descriptors: Block bitmap for group 880 not in group (block 0)!
Dec  2 14:00:00 localhost kernel: [4298880.221000] EXT3-fs: group descriptors corrupted !
Dec  2 14:00:00 localhost kernel: [4298880.228000] EXT2-fs error (device sda): ext2_check_descriptors: Block bitmap for group 880 not in group (block 0)!
Dec  2 14:00:00 localhost kernel: [4298880.228000] EXT2-fs: group descriptors corrupted!
Dec  2 14:00:00 localhost kernel: [4298880.239000] EXT2-fs error (device sda): ext2_check_descriptors: Block bitmap for group 880 not in group (block 0)!
Dec  2 14:00:00 localhost kernel: [4298880.239000] EXT2-fs: group descriptors corrupted!
Dec  2 14:00:01 localhost kernel: [4298880.246000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
Dec  2 14:00:01 localhost kernel: [4298880.248000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
Dec  2 14:00:01 localhost kernel: [4298880.250000] XFS: bad magic number
Dec  2 14:00:01 localhost kernel: [4298880.250000] XFS: SB validate failed
Dec  2 14:00:01 localhost kernel: [4298880.253000] XFS: bad magic number
Dec  2 14:00:01 localhost kernel: [4298880.253000] XFS: SB validate failed
Dec  2 14:00:01 localhost usbmount[14315]: cannnot execute /sbin/udev_volume_id

---

### Post by HermanAB on 2005-12-03
This schtuff is handled by the udev file system. There are a few good articles on it:
[http://gobo.kundor.org/kb/index.php/Udev%20Howto](http://gobo.kundor.org/kb/index.php/Udev%20Howto)
[http://wiki.archlinux.org/index.php/UdevHowTo](http://wiki.archlinux.org/index.php/UdevHowTo)

Cheers,

Herman
[http://www.aerospacesoftware.com/](http://www.aerospacesoftware.com/)

---

### Post by reagle on 2005-12-05
Well, that's confirms udev is seeing sda (and not sda1 apparently from the output below) but I don't know what to do about it.

device '/sys/block/sda' has major:minor 8:0
  looking at class device '/sys/block/sda':
    SUBSYSTEM=="block"
    SYSFS{dev}=="8:0"
    SYSFS{range}=="16"
    SYSFS{removable}=="0"
    SYSFS{size}=="234441648"
    SYSFS{stat}=="     412      118     1803      852        9        1       80
       15        0      654      867"

---


---
title: "Grub2 - Build error"
date: 2016-05-12
forum: Desktop Environments
---

### Post by stolas2 on 2016-05-12
Hi !

I would like to delete all the text on Grub2 (header, menu and footer) to display only a black screen. So I use this thread : [http://unix.stackexchange.com/questions … n-advanced]("http://unix.stackexchange.com/questions/127744/grub-modify-menu-screen-advanced").
I try to compile GRUB 2.02~beta2-29ubuntu0.3 to remove the header and footer but I get two errors:
FAIL: ext234_test
FAIL: ntfs_test

If I do any changes and I try to compile, I have the same errors.

Can you help me ? [IMG]https://bbs.archlinux.org/img/smilies/smile.png[/IMG]

Here is the full report:

```

make  check-TESTS
make[5]: Entering directory '/home/stolas/srccode/grub2-2.02~beta2/obj/grub-pc'
make[6]: Entering directory '/home/stolas/srccode/grub2-2.02~beta2/obj/grub-pc'
PASS: example_unit_test
PASS: printf_test
PASS: date_test
PASS: priority_queue_unit_test
PASS: cmp_test
FAIL: ext234_test
SKIP: squashfs_test
PASS: iso9660_test
SKIP: hfsplus_test
FAIL: ntfs_test
SKIP: reiserfs_test
PASS: fat_test
SKIP: minixfs_test
SKIP: xfs_test
SKIP: nilfs2_test
SKIP: romfs_test
SKIP: exfat_test
PASS: tar_test
SKIP: udf_test
SKIP: hfs_test
SKIP: jfs_test
SKIP: btrfs_test
SKIP: zfs_test
PASS: cpio_test
PASS: example_scripted_test
SKIP: gettext_strings_test
PASS: pata_test
PASS: ahci_test
PASS: uhci_test
PASS: ohci_test
PASS: ehci_test
PASS: example_grub_script_test
PASS: grub_script_eval
PASS: grub_script_test
PASS: grub_script_echo1
PASS: grub_script_leading_whitespace
PASS: grub_script_echo_keywords
PASS: grub_script_vars1
PASS: grub_script_for1
PASS: grub_script_while1
PASS: grub_script_if
PASS: grub_script_blanklines
PASS: grub_script_final_semicolon
PASS: grub_script_dollar
PASS: grub_script_comments
PASS: grub_script_functions
PASS: grub_script_break
PASS: grub_script_continue
PASS: grub_script_shift
PASS: grub_script_blockarg
PASS: grub_script_setparams
PASS: grub_script_return
PASS: grub_cmd_regexp
PASS: grub_cmd_date
PASS: grub_cmd_set_date
PASS: grub_cmd_sleep
PASS: grub_script_expansion
PASS: grub_script_not
PASS: grub_script_no_commands
PASS: partmap_test
PASS: hddboot_test
PASS: fddboot_test
PASS: cdboot_test
PASS: netboot_test
PASS: pseries_test
PASS: core_compress_test
PASS: xzcompress_test
PASS: gzcompress_test
SKIP: lzocompress_test
PASS: grub_cmd_echo
PASS: help_test
PASS: grub_script_gettext
PASS: grub_script_escape_comma
PASS: grub_script_strcmp
PASS: test_sha512sum
PASS: test_unset
PASS: grub_func_test
PASS: grub_cmd_tr
===================================================
   GRUB 2.02~beta2-29ubuntu0.3: ./test-suite.log
===================================================

# TOTAL: 78
# PASS:  61
# SKIP:  15
# XFAIL: 0
# FAIL:  2
# XPASS: 0
# ERROR: 0

.. contents:: :depth: 2

FAIL: ext234_test
=================

Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ext* - Label `g;/é&#1090; &#194971;&#128513;' - Last modification time 2016-05-11 07:28:55 Wednesday, UUID 1befa6f3-44b1-49d1-94b9-797a345ada71 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.yVZt9sH50Q/ext2_old_rw: not mounted
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ext* - Label `g;/é&#1090; &#194971;&#128513;' - Last modification time 2016-05-11 07:29:03 Wednesday, UUID 145f051f-6388-48af-b250-971fdca0d486 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.yVZt9sH50Q/ext2_old_rw: not mounted
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ext* - Label `g;/é&#1090; &#194971;&#128513;' - Last modification time 2016-05-11 07:29:10 Wednesday, UUID 78e3ccc3-e255-484b-ab5b-4160383dbc3a - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.yVZt9sH50Q/ext2_old_rw: not mounted
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ext* - Label `g;/é&#1090; &#194971;&#128513;' - Last modification time 2016-05-11 07:29:23 Wednesday, UUID be7f535c-536a-42d3-bf9d-de297b26da3d - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.yVZt9sH50Q/ext2_old_rw: not mounted
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ext* - Label `g;/é&#1090; &#194971;&#128513;' - Last modification time 2016-05-11 07:29:31 Wednesday, UUID 5b16fe56-427d-44c6-9180-fa11e92b64dc - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.yVZt9sH50Q/ext2_old_rw: not mounted
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ext* - Label `g;/é&#1090; &#194971;&#128513;' - Last modification time 2016-05-11 07:29:38 Wednesday, UUID 99f80428-cc52-485a-a2da-73def574fb4a - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.yVZt9sH50Q/ext2_old_rw: not mounted
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ext* - Label `g;/é&#1090; &#194971;&#128513;' - Last modification time 2016-05-11 07:29:51 Wednesday, UUID fad113c3-96fe-419e-829b-79c292a39865 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.yVZt9sH50Q/ext2_old_rw: not mounted
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ext* - Label `g;/é&#1090; &#194971;&#128513;' - Last modification time 2016-05-11 07:29:59 Wednesday, UUID 60ed5905-1fb3-4966-a376-e128455ef0f0 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.yVZt9sH50Q/ext2_old_rw: not mounted
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ext* - Label `g;/é&#1090; &#194971;&#128513;' - Last modification time 2016-05-11 07:30:06 Wednesday, UUID dcfbffc6-af8f-4c7d-9f8c-a994e58ae3a2 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.yVZt9sH50Q/ext2_old_rw: not mounted
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ext* - Label `g;/é&#1090; &#194971;&#128513;' - Last modification time 2016-05-11 07:30:14 Wednesday, UUID d2da5b71-37bc-4cba-b8ed-b202c9e0b20b - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.yVZt9sH50Q/ext2_old_rw: not mounted
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ext* - Label `g;/é&#1090; &#194971;&#128513;' - Last modification time 2016-05-11 07:30:21 Wednesday, UUID 2d9b806b-a9ce-48c0-a7bc-4d2a68a97ca8 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.yVZt9sH50Q/ext2_old_rw: not mounted
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ext* - Label `g;/é&#1090; &#194971;&#128513;' - Last modification time 2016-05-11 07:30:27 Wednesday, UUID 5b42f36b-69e2-420a-89bf-5144c20e0ad3 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.yVZt9sH50Q/ext2_old_rw: not mounted
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ext* - Label `g;/é&#1090; &#194971;&#128513;' - Last modification time 2016-05-11 07:30:41 Wednesday, UUID 758c6777-462b-42b9-b9f7-22cac08f61f9 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.sXKTfnzmdC/ext2_rw: not mounted
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ext* - Label `g;/é&#1090; &#194971;&#128513;' - Last modification time 2016-05-11 07:30:50 Wednesday, UUID 8b517eb2-67cf-4b86-aacf-46b01201a250 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.sXKTfnzmdC/ext2_rw: not mounted
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ext* - Label `g;/é&#1090; &#194971;&#128513;' - Last modification time 2016-05-11 07:30:57 Wednesday, UUID 65c3265b-0443-452c-956f-6a4e8c1b76ba - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.sXKTfnzmdC/ext2_rw: not mounted
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ext* - Label `g;/é&#1090; &#194971;&#128513;' - Last modification time 2016-05-11 07:31:10 Wednesday, UUID f0176e70-7405-48b5-b904-7c0b7edc8b1b - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.sXKTfnzmdC/ext2_rw: not mounted
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ext* - Label `g;/é&#1090; &#194971;&#128513;' - Last modification time 2016-05-11 07:31:19 Wednesday, UUID 9ab79051-6595-4993-affa-eb440ecde619 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.sXKTfnzmdC/ext2_rw: not mounted
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ext* - Label `g;/é&#1090; &#194971;&#128513;' - Last modification time 2016-05-11 07:31:26 Wednesday, UUID 17c79c18-f21d-4176-8710-0743ebbd63cb - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.sXKTfnzmdC/ext2_rw: not mounted
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ext* - Label `g;/é&#1090; &#194971;&#128513;' - Last modification time 2016-05-11 07:31:39 Wednesday, UUID 5977bfd0-20b7-4f97-9a77-9cce7f77aa68 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.sXKTfnzmdC/ext2_rw: not mounted
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ext* - Label `g;/é&#1090; &#194971;&#128513;' - Last modification time 2016-05-11 07:31:47 Wednesday, UUID 6184f94d-4606-4d52-aa74-560a93990a92 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.sXKTfnzmdC/ext2_rw: not mounted
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ext* - Label `g;/é&#1090; &#194971;&#128513;' - Last modification time 2016-05-11 07:31:55 Wednesday, UUID 7d2ce503-c8e1-48a4-b86c-0b096a744d6e - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.sXKTfnzmdC/ext2_rw: not mounted
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ext* - Label `g;/é&#1090; &#194971;&#128513;' - Last modification time 2016-05-11 07:32:03 Wednesday, UUID 4c38a0c8-66b4-4a4b-a0bf-62302ec82ed2 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.sXKTfnzmdC/ext2_rw: not mounted
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ext* - Label `g;/é&#1090; &#194971;&#128513;' - Last modification time 2016-05-11 07:32:11 Wednesday, UUID 768e8a35-50ed-4a03-a13f-1a63ab3e2775 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

./grub-fstest: error: OS file /tmp/tmp.sXKTfnzmdC/ext2_ro//////sdir/////2.img open error: Not a directory.
SDIR SYMLINK FAIL

SKIP: squashfs_test
===================

mksquashfs not installed; cannot test squashfs.

SKIP: hfsplus_test
==================

mkfs.hfsplus not installed; cannot test hfsplus.

FAIL: ntfs_test
===============

The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ntfs - Label `grub_;/testé&#1090;i u&#194971;&#128513;&#194969;&#1082;&#1080;&#1088;&#1080;rewfceniuewruevrewnuuireurevueurnievrewfnerfcnevirivinrewvniwnivrewiuvcrewvnuewvrrrewniureifiuewifjiww', UUID 652CB14262185B2A - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.57BEYJqrz1/ntfs_rw: not mounted
The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ntfs - Label `grub_;/testé&#1090;i u&#194971;&#128513;&#194969;&#1082;&#1080;&#1088;&#1080;rewfceniuewruevrewnuuireurevueurnievrewfnerfcnevirivinrewvniwnivrewiuvcrewvnuewvrrrewniureifiuewifjiww', UUID 3856060B1F5316ED - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.57BEYJqrz1/ntfs_rw: not mounted
The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ntfs - Label `grub_;/testé&#1090;i u&#194971;&#128513;&#194969;&#1082;&#1080;&#1088;&#1080;rewfceniuewruevrewnuuireurevueurnievrewfnerfcnevirivinrewvniwnivrewiuvcrewvnuewvrrrewniureifiuewifjiww', UUID 4B52825F5C1B56A9 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.57BEYJqrz1/ntfs_rw: not mounted
The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ntfs - Label `grub_;/testé&#1090;i u&#194971;&#128513;&#194969;&#1082;&#1080;&#1088;&#1080;rewfceniuewruevrewnuuireurevueurnievrewfnerfcnevirivinrewvniwnivrewiuvcrewvnuewvrrrewniureifiuewifjiww', UUID 1F5971451A23E9F3 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.57BEYJqrz1/ntfs_rw: not mounted
The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
Windows cannot use compression when the cluster size is larger than 4096 bytes.  Compression has been disabled for this volume.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ntfs - Label `grub_;/testé&#1090;i u&#194971;&#128513;&#194969;&#1082;&#1080;&#1088;&#1080;rewfceniuewruevrewnuuireurevueurnievrewfnerfcnevirivinrewvniwnivrewiuvcrewvnuewvrrrewniureifiuewifjiww', UUID 5F7602830B60230A - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.57BEYJqrz1/ntfs_rw: not mounted
The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
Windows cannot use compression when the cluster size is larger than 4096 bytes.  Compression has been disabled for this volume.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ntfs - Label `grub_;/testé&#1090;i u&#194971;&#128513;&#194969;&#1082;&#1080;&#1088;&#1080;rewfceniuewruevrewnuuireurevueurnievrewfnerfcnevirivinrewvniwnivrewiuvcrewvnuewvrrrewniureifiuewifjiww', UUID 738175EB4973EE46 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.57BEYJqrz1/ntfs_rw: not mounted
The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
Windows cannot use compression when the cluster size is larger than 4096 bytes.  Compression has been disabled for this volume.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ntfs - Label `grub_;/testé&#1090;i u&#194971;&#128513;&#194969;&#1082;&#1080;&#1088;&#1080;rewfceniuewruevrewnuuireurevueurnievrewfnerfcnevirivinrewvniwnivrewiuvcrewvnuewvrrrewniureifiuewifjiww', UUID 473B5B7E07504A48 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.57BEYJqrz1/ntfs_rw: not mounted
The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ntfs - Label `grub_;/testé&#1090;i u&#194971;&#128513;&#194969;&#1082;&#1080;&#1088;&#1080;rewfceniuewruevrewnuuireurevueurnievrewfnerfcnevirivinrewvniwnivrewiuvcrewvnuewvrrrewniureifiuewifjiww', UUID 07970D0F7892859B - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.57BEYJqrz1/ntfs_rw: not mounted
The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ntfs - Label `grub_;/testé&#1090;i u&#194971;&#128513;&#194969;&#1082;&#1080;&#1088;&#1080;rewfceniuewruevrewnuuireurevueurnievrewfnerfcnevirivinrewvniwnivrewiuvcrewvnuewvrrrewniureifiuewifjiww', UUID 1AF0A69035D123C9 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.57BEYJqrz1/ntfs_rw: not mounted
The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ntfs - Label `grub_;/testé&#1090;i u&#194971;&#128513;&#194969;&#1082;&#1080;&#1088;&#1080;rewfceniuewruevrewnuuireurevueurnievrewfnerfcnevirivinrewvniwnivrewiuvcrewvnuewvrrrewniureifiuewifjiww', UUID 5BB42CEB679B4755 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.57BEYJqrz1/ntfs_rw: not mounted
The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ntfs - Label `grub_;/testé&#1090;i u&#194971;&#128513;&#194969;&#1082;&#1080;&#1088;&#1080;rewfceniuewruevrewnuuireurevueurnievrewfnerfcnevirivinrewvniwnivrewiuvcrewvnuewvrrrewniureifiuewifjiww', UUID 6F6D030A25571A7C - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.57BEYJqrz1/ntfs_rw: not mounted
The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
Windows cannot use compression when the cluster size is larger than 4096 bytes.  Compression has been disabled for this volume.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ntfs - Label `grub_;/testé&#1090;i u&#194971;&#128513;&#194969;&#1082;&#1080;&#1088;&#1080;rewfceniuewruevrewnuuireurevueurnievrewfnerfcnevirivinrewvniwnivrewiuvcrewvnuewvrrrewniureifiuewifjiww', UUID 708E54CD178C5810 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.57BEYJqrz1/ntfs_rw: not mounted
The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
Windows cannot use compression when the cluster size is larger than 4096 bytes.  Compression has been disabled for this volume.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ntfs - Label `grub_;/testé&#1090;i u&#194971;&#128513;&#194969;&#1082;&#1080;&#1088;&#1080;rewfceniuewruevrewnuuireurevueurnievrewfnerfcnevirivinrewvniwnivrewiuvcrewvnuewvrrrewniureifiuewifjiww', UUID 4445CD9D55234358 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.57BEYJqrz1/ntfs_rw: not mounted
The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
Windows cannot use compression when the cluster size is larger than 4096 bytes.  Compression has been disabled for this volume.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ntfs - Label `grub_;/testé&#1090;i u&#194971;&#128513;&#194969;&#1082;&#1080;&#1088;&#1080;rewfceniuewruevrewnuuireurevueurnievrewfnerfcnevirivinrewvniwnivrewiuvcrewvnuewvrrrewniureifiuewifjiww', UUID 44A72D0D46BD733B - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.57BEYJqrz1/ntfs_rw: not mounted
The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
Windows cannot use compression when the cluster size is larger than 4096 bytes.  Compression has been disabled for this volume.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ntfs - Label `grub_;/testé&#1090;i u&#194971;&#128513;&#194969;&#1082;&#1080;&#1088;&#1080;rewfceniuewruevrewnuuireurevueurnievrewfnerfcnevirivinrewvniwnivrewiuvcrewvnuewvrrrewniureifiuewifjiww', UUID 57108C6C42D57337 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.57BEYJqrz1/ntfs_rw: not mounted
The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ntfs - Label `grub_;/testé&#1090;i u&#194971;&#128513;&#194969;&#1082;&#1080;&#1088;&#1080;rewfceniuewruevrewnuuireurevueurnievrewfnerfcnevirivinrewvniwnivrewiuvcrewvnuewvrrrewniureifiuewifjiww', UUID 1962200076688192 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.57BEYJqrz1/ntfs_rw: not mounted
The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ntfs - Label `grub_;/testé&#1090;i u&#194971;&#128513;&#194969;&#1082;&#1080;&#1088;&#1080;rewfceniuewruevrewnuuireurevueurnievrewfnerfcnevirivinrewvniwnivrewiuvcrewvnuewvrrrewniureifiuewifjiww', UUID 6B904344327EC0AE - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.57BEYJqrz1/ntfs_rw: not mounted
The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ntfs - Label `grub_;/testé&#1090;i u&#194971;&#128513;&#194969;&#1082;&#1080;&#1088;&#1080;rewfceniuewruevrewnuuireurevueurnievrewfnerfcnevirivinrewvniwnivrewiuvcrewvnuewvrrrewniureifiuewifjiww', UUID 7F1008502FF388B6 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.57BEYJqrz1/ntfs_rw: not mounted
The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
Windows cannot use compression when the cluster size is larger than 4096 bytes.  Compression has been disabled for this volume.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ntfs - Label `grub_;/testé&#1090;i u&#194971;&#128513;&#194969;&#1082;&#1080;&#1088;&#1080;rewfceniuewruevrewnuuireurevueurnievrewfnerfcnevirivinrewvniwnivrewiuvcrewvnuewvrrrewniureifiuewifjiww', UUID 409DD88D22A58EF3 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.57BEYJqrz1/ntfs_rw: not mounted
The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
Windows cannot use compression when the cluster size is larger than 4096 bytes.  Compression has been disabled for this volume.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ntfs - Label `grub_;/testé&#1090;i u&#194971;&#128513;&#194969;&#1082;&#1080;&#1088;&#1080;rewfceniuewruevrewnuuireurevueurnievrewfnerfcnevirivinrewvniwnivrewiuvcrewvnuewvrrrewniureifiuewifjiww', UUID 53B8C4085FC12964 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.57BEYJqrz1/ntfs_rw: not mounted
The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
Windows cannot use compression when the cluster size is larger than 4096 bytes.  Compression has been disabled for this volume.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ntfs - Label `grub_;/testé&#1090;i u&#194971;&#128513;&#194969;&#1082;&#1080;&#1088;&#1080;rewfceniuewruevrewnuuireurevueurnievrewfnerfcnevirivinrewvniwnivrewiuvcrewvnuewvrrrewniureifiuewifjiww', UUID 26E638A15D1137D2 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.57BEYJqrz1/ntfs_rw: not mounted
The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
Windows cannot use compression when the cluster size is larger than 4096 bytes.  Compression has been disabled for this volume.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ntfs - Label `grub_;/testé&#1090;i u&#194971;&#128513;&#194969;&#1082;&#1080;&#1088;&#1080;rewfceniuewruevrewnuuireurevueurnievrewfnerfcnevirivinrewvniwnivrewiuvcrewvnuewvrrrewniureifiuewifjiww', UUID 6757D76F4E48C383 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.57BEYJqrz1/ntfs_rw: not mounted
The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ntfs - Label `grub_;/testé&#1090;i u&#194971;&#128513;&#194969;&#1082;&#1080;&#1088;&#1080;rewfceniuewruevrewnuuireurevueurnievrewfnerfcnevirivinrewvniwnivrewiuvcrewvnuewvrrrewniureifiuewifjiww', UUID 3B5FB4A24C54FC45 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.57BEYJqrz1/ntfs_rw: not mounted
The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ntfs - Label `grub_;/testé&#1090;i u&#194971;&#128513;&#194969;&#1082;&#1080;&#1088;&#1080;rewfceniuewruevrewnuuireurevueurnievrewfnerfcnevirivinrewvniwnivrewiuvcrewvnuewvrrrewniureifiuewifjiww', UUID 3C4405F67E40B83E - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.57BEYJqrz1/ntfs_rw: not mounted
The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
Windows cannot use compression when the cluster size is larger than 4096 bytes.  Compression has been disabled for this volume.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ntfs - Label `grub_;/testé&#1090;i u&#194971;&#128513;&#194969;&#1082;&#1080;&#1088;&#1080;rewfceniuewruevrewnuuireurevueurnievrewfnerfcnevirivinrewvniwnivrewiuvcrewvnuewvrrrewniureifiuewifjiww', UUID 100534413C0EBA76 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.57BEYJqrz1/ntfs_rw: not mounted
The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
Windows cannot use compression when the cluster size is larger than 4096 bytes.  Compression has been disabled for this volume.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ntfs - Label `grub_;/testé&#1090;i u&#194971;&#128513;&#194969;&#1082;&#1080;&#1088;&#1080;rewfceniuewruevrewnuuireurevueurnievrewfnerfcnevirivinrewvniwnivrewiuvcrewvnuewvrrrewniureifiuewifjiww', UUID 63632B8A39B21E49 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.57BEYJqrz1/ntfs_rw: not mounted
The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
Windows cannot use compression when the cluster size is larger than 4096 bytes.  Compression has been disabled for this volume.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ntfs - Label `grub_;/testé&#1090;i u&#194971;&#128513;&#194969;&#1082;&#1080;&#1088;&#1080;rewfceniuewruevrewnuuireurevueurnievrewfnerfcnevirivinrewvniwnivrewiuvcrewvnuewvrrrewniureifiuewifjiww', UUID 64C7C5222BD855E4 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.57BEYJqrz1/ntfs_rw: not mounted
The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
Windows cannot use compression when the cluster size is larger than 4096 bytes.  Compression has been disabled for this volume.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ntfs - Label `grub_;/testé&#1090;i u&#194971;&#128513;&#194969;&#1082;&#1080;&#1088;&#1080;rewfceniuewruevrewnuuireurevueurnievrewfnerfcnevirivinrewvniwnivrewiuvcrewvnuewvrrrewniureifiuewifjiww', UUID 3788061568890C0D - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.57BEYJqrz1/ntfs_rw: not mounted
The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ntfs - Label `grub_;/testé&#1090;i u&#194971;&#128513;&#194969;&#1082;&#1080;&#1088;&#1080;rewfceniuewruevrewnuuireurevueurnievrewfnerfcnevirivinrewvniwnivrewiuvcrewvnuewvrrrewniureifiuewifjiww', UUID 0A7F5D97656BD7AA - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.57BEYJqrz1/ntfs_rw: not mounted
The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
Windows cannot use compression when the cluster size is larger than 4096 bytes.  Compression has been disabled for this volume.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ntfs - Label `grub_;/testé&#1090;i u&#194971;&#128513;&#194969;&#1082;&#1080;&#1088;&#1080;rewfceniuewruevrewnuuireurevueurnievrewfnerfcnevirivinrewvniwnivrewiuvcrewvnuewvrrrewniureifiuewifjiww', UUID 0BF7140E17F3DE0E - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.57BEYJqrz1/ntfs_rw: not mounted
The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
Windows cannot use compression when the cluster size is larger than 4096 bytes.  Compression has been disabled for this volume.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ntfs - Label `grub_;/testé&#1090;i u&#194971;&#128513;&#194969;&#1082;&#1080;&#1088;&#1080;rewfceniuewruevrewnuuireurevueurnievrewfnerfcnevirivinrewvniwnivrewiuvcrewvnuewvrrrewniureifiuewifjiww', UUID 1F191E261538ABF1 - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.57BEYJqrz1/ntfs_rw: not mounted
The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
Windows cannot use compression when the cluster size is larger than 4096 bytes.  Compression has been disabled for this volume.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ntfs - Label `grub_;/testé&#1090;i u&#194971;&#128513;&#194969;&#1082;&#1080;&#1088;&#1080;rewfceniuewruevrewnuuireurevueurnievrewfnerfcnevirivinrewvniwnivrewiuvcrewvnuewvrrrewniureifiuewifjiww', UUID 322F16B41241E83A - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.57BEYJqrz1/ntfs_rw: not mounted
The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
Windows cannot use compression when the cluster size is larger than 4096 bytes.  Compression has been disabled for this volume.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Device proc: Filesystem type procfs - Sector size 512B - Total size 0KiB
Device loop0: Filesystem type ntfs - Label `grub_;/testé&#1090;i u&#194971;&#128513;&#194969;&#1082;&#1080;&#1088;&#1080;rewfceniuewruevrewnuuireurevueurnievrewfnerfcnevirivinrewvniwnivrewiuvcrewvnuewvrrrewniureifiuewifjiww', UUID 73B6AE1B04E6EDAC - Sector size 512B - Total size 5939200KiB
Device host: Filesystem type hostfs - Sector size 512B - Total size 0KiB

umount: /tmp/tmp.57BEYJqrz1/ntfs_rw: not mounted
The partition start sector was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/loop1 and it could not be obtained automatically.  It has been set to 0.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
./grub-fs-tester: line 895: setfattr: command not found

SKIP: reiserfs_test
===================

mkfs.reiserfs not installed; cannot test reiserfs.

SKIP: minixfs_test
==================

mkfs.minix: Usage: mkfs.minix [-c | -l filename] [-nXX] [-iXX] /dev/name [blocks]
mkfs.minix doesn't support minix3fs; cannot test minix*fs.

SKIP: xfs_test
==============

mkfs.xfs not installed; cannot test xfs.

SKIP: nilfs2_test
=================

mkfs.nilfs2 not installed; cannot test nilfs2.

SKIP: romfs_test
================

genromfs not installed; cannot test romfs.

SKIP: exfat_test
================

mkfs.exfat not installed; cannot test exFAT.

SKIP: udf_test
==============

mkudffs not installed; cannot test UDF.

SKIP: hfs_test
==============

mkfs.hfs not installed; cannot test HFS.

SKIP: jfs_test
==============

mkfs.jfs not installed; cannot test JFS.

SKIP: btrfs_test
================

mkfs.btrfs not installed; cannot test btrfs.

SKIP: zfs_test
==============

zpool not installed; cannot test zfs.

SKIP: gettext_strings_test
==========================

Skipping upstream maintenance check.

SKIP: lzocompress_test
======================

lzop not installed; cannot test lzo compression.

============================================================================
Testsuite summary for GRUB 2.02~beta2-29ubuntu0.3
============================================================================
# TOTAL: 78
# PASS:  61
# SKIP:  15
# XFAIL: 0
# FAIL:  2
# XPASS: 0
# ERROR: 0
============================================================================
See ./test-suite.log
Please report to bug-grub@gnu.org
============================================================================
Makefile:11764: recipe for target 'test-suite.log' failed
make[6]: *** [test-suite.log] Error 1
make[6]: Leaving directory '/home/stolas/srccode/grub2-2.02~beta2/obj/grub-pc'
Makefile:11870: recipe for target 'check-TESTS' failed
make[5]: *** [check-TESTS] Error 2
make[5]: Leaving directory '/home/stolas/srccode/grub2-2.02~beta2/obj/grub-pc'
Makefile:12640: recipe for target 'check-am' failed
make[4]: *** [check-am] Error 2
make[4]: Leaving directory '/home/stolas/srccode/grub2-2.02~beta2/obj/grub-pc'
Makefile:11650: recipe for target 'check-recursive' failed
make[3]: *** [check-recursive] Error 1
make[3]: Leaving directory '/home/stolas/srccode/grub2-2.02~beta2/obj/grub-pc'
Makefile:12643: recipe for target 'check' failed
make[2]: *** [check] Error 2
make[2]: Leaving directory '/home/stolas/srccode/grub2-2.02~beta2/obj/grub-pc'
dh_auto_test: make -j1 check returned exit code 2
debian/rules:215: recipe for target 'debian/stamps/build-grub-pc' failed
make[1]: *** [debian/stamps/build-grub-pc] Error 2
make[1]: Leaving directory '/home/stolas/srccode/grub2-2.02~beta2'
debian/rules:112: recipe for target 'build' failed
make: *** [build] Error 2
dpkg-buildpackage: erreur: debian/rules build a produit une erreur de sortie de type 2

```

---


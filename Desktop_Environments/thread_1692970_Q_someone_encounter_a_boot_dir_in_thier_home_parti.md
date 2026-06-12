---
title: "Q: someone encounter a boot dir in thier home partition in ubuntu lucyd"
date: 2011-02-22
forum: Desktop Environments
---

### Post by jao_madn on 2011-02-22
Hi

This evening i encounter about this directory in my home partition in my  ubuntu lucyd..My home patition has an boot directory in it..i didn't  create this one when i install or even separate my boot directory to  other partition i stick to default the /boot/grub is installed in the  main root partition.

Here i paste the contain of the /home/boot/grub/*
-rw-r--r-- 1 root root  8304 2011-01-12 11:41 915resolution.mod
-rw-r--r-- 1 root root 10624 2011-01-12 11:41 acpi.mod
-rw-r--r-- 1 root root  4640 2011-01-12 11:41 affs.mod
-rw-r--r-- 1 root root  4932 2011-01-12 11:41 afs_be.mod
-rw-r--r-- 1 root root  4912 2011-01-12 11:41 afs.mod
-rw-r--r-- 1 root root  1136 2011-01-12 11:41 aout.mod
-rw-r--r-- 1 root root  8136 2011-01-12 11:41 ata.mod
-rw-r--r-- 1 root root  2344 2011-01-12 11:41 ata_pthru.mod
-rw-r--r-- 1 root root  2768 2011-01-12 11:41 at_keyboard.mod
-rw-r--r-- 1 root root  4828 2011-01-12 11:41 befs_be.mod
-rw-r--r-- 1 root root  4800 2011-01-12 11:41 befs.mod
-rw-r--r-- 1 root root  4388 2011-01-12 11:41 biosdisk.mod
-rw-r--r-- 1 root root  2500 2011-01-12 11:41 bitmap.mod
-rw-r--r-- 1 root root  2996 2011-01-12 11:41 bitmap_scale.mod
-rw-r--r-- 1 root root  2104 2011-01-12 11:41 blocklist.mod
-rw-r--r-- 1 root root   512 2011-01-12 11:41 boot.img
-rw-r--r-- 1 root root  2652 2011-01-12 11:41 boot.mod
-rw-r--r-- 1 root root 19824 2011-01-12 11:41 bsd.mod
-rw-r--r-- 1 root root  2048 2011-01-12 11:41 bufio.mod
-rw-r--r-- 1 root root  2072 2011-01-12 11:41 cat.mod
-rw-r--r-- 1 root root   512 2011-01-12 11:41 cdboot.img
-rw-r--r-- 1 root root  2504 2011-01-12 11:41 chain.mod
-rw-r--r-- 1 root root  2036 2011-01-12 11:41 charset.mod
-rw-r--r-- 1 root root  2228 2011-01-12 11:41 cmp.mod
-rw-r--r-- 1 root root  1950 2011-01-12 11:41 command.lst
-rw-r--r-- 1 root root  1876 2011-01-12 11:41 configfile.mod
-rw-r--r-- 1 root root 24748 2011-01-12 11:41 core.img
-rw-r--r-- 1 root root  2892 2011-01-12 11:41 cpio.mod
-rw-r--r-- 1 root root  1696 2011-01-12 11:41 cpuid.mod
-rw-r--r-- 1 root root  1868 2011-01-12 11:41 crc.mod
-rw-r--r-- 1 root root   825 2011-01-12 11:41 crypto.lst
-rw-r--r-- 1 root root  4472 2011-01-12 11:41 crypto.mod
-rw-r--r-- 1 root root  1916 2011-01-12 11:41 datehook.mod
-rw-r--r-- 1 root root  2404 2011-01-12 11:41 date.mod
-rw-r--r-- 1 root root  1333 2011-01-12 11:41 datetime.mod
-rw-r--r-- 1 root root   512 2011-01-12 11:41 diskboot.img
-rw-r--r-- 1 root root  1952 2011-01-12 11:41 dm_nv.mod
-rw-r--r-- 1 root root  5616 2011-01-12 11:41 drivemap.mod
-rw-r--r-- 1 root root  2004 2011-01-12 11:41 echo.mod
-rw-r--r-- 1 root root  6444 2011-01-12 11:41 efiemu32.o
-rw-r--r-- 1 root root 11010 2011-01-12 11:41 efiemu64.o
-rw-r--r-- 1 root root 24484 2011-01-12 11:41 efiemu.mod
-rw-r--r-- 1 root root  4512 2011-01-12 11:41 elf.mod
-rw-r--r-- 1 root root  1764 2011-01-12 11:41 example_functional_test.mod
-rw-r--r-- 1 root root  5532 2011-01-12 11:41 ext2.mod
-rw-r--r-- 1 root root  4092 2011-01-12 11:41 extcmd.mod
-rw-r--r-- 1 root root  5996 2011-01-12 11:41 fat.mod
-rw-r--r-- 1 root root  9820 2011-01-12 11:41 font.mod
-rw-r--r-- 1 root root  2852 2011-01-12 11:41 fshelp.mod
-rw-r--r-- 1 root root   121 2011-01-12 11:41 fs.lst
-rw-r--r-- 1 root root  2704 2011-01-12 11:41 functional_test.mod
-rw-r--r-- 1 root root  1860 2011-01-12 11:41 gcry_arcfour.mod
-rw-r--r-- 1 root root  8240 2011-01-12 11:41 gcry_blowfish.mod
-rw-r--r-- 1 root root 35136 2011-01-12 11:41 gcry_camellia.mod
-rw-r--r-- 1 root root 17660 2011-01-12 11:41 gcry_cast5.mod
-rw-r--r-- 1 root root  3080 2011-01-12 11:41 gcry_crc.mod
-rw-r--r-- 1 root root 19368 2011-01-12 11:41 gcry_des.mod
-rw-r--r-- 1 root root  3360 2011-01-12 11:41 gcry_md4.mod
-rw-r--r-- 1 root root  4104 2011-01-12 11:41 gcry_md5.mod
-rw-r--r-- 1 root root  2728 2011-01-12 11:41 gcry_rfc2268.mod
-rw-r--r-- 1 root root 19300 2011-01-12 11:41 gcry_rijndael.mod
-rw-r--r-- 1 root root  9228 2011-01-12 11:41 gcry_rmd160.mod
-rw-r--r-- 1 root root 16744 2011-01-12 11:41 gcry_seed.mod
-rw-r--r-- 1 root root 18132 2011-01-12 11:41 gcry_serpent.mod
-rw-r--r-- 1 root root  9016 2011-01-12 11:41 gcry_sha1.mod
-rw-r--r-- 1 root root  3584 2011-01-12 11:41 gcry_sha256.mod
-rw-r--r-- 1 root root  5768 2011-01-12 11:41 gcry_sha512.mod
-rw-r--r-- 1 root root 12088 2011-01-12 11:41 gcry_tiger.mod
-rw-r--r-- 1 root root 39708 2011-01-12 11:41 gcry_twofish.mod
-rw-r--r-- 1 root root 24920 2011-01-12 11:41 gcry_whirlpool.mod
-rw-r--r-- 1 root root  4064 2011-01-12 11:41 gettext.mod
-rw-r--r-- 1 root root 37404 2011-01-12 11:41 gfxmenu.mod
-rw-r--r-- 1 root root 11040 2011-01-12 11:41 gfxterm.mod
-rw-r--r-- 1 root root  3808 2011-01-12 11:41 gptsync.mod
-rw-r--r-- 1 root root 10240 2011-01-12 11:41 grldr.img
-rw-r--r-- 1 root root  1024 2011-01-12 11:41 grubenv
-rw-r--r-- 1 root root  7824 2011-01-12 11:41 gzio.mod
-rw-r--r-- 1 root root  1548 2011-01-12 11:41 halt.mod
-rw-r--r-- 1 root root    16 2011-01-12 11:41 handler.lst
-rw-r--r-- 1 root root  1776 2011-01-12 11:41 handler.mod
-rw-r--r-- 1 root root  4808 2011-01-12 11:41 hashsum.mod
-rw-r--r-- 1 root root  7508 2011-01-12 11:41 hdparm.mod
-rw-r--r-- 1 root root  1304 2011-01-12 11:41 hello.mod
-rw-r--r-- 1 root root  2500 2011-01-12 11:41 help.mod
-rw-r--r-- 1 root root  3328 2011-01-12 11:41 hexdump.mod
-rw-r--r-- 1 root root  6068 2011-01-12 11:41 hfs.mod
-rw-r--r-- 1 root root  5932 2011-01-12 11:41 hfsplus.mod
-rw-r--r-- 1 root root  6292 2011-01-12 11:41 iso9660.mod
-rw-r--r-- 1 root root  5832 2011-01-12 11:41 jfs.mod
-rw-r--r-- 1 root root  5988 2011-01-12 11:41 jpeg.mod
-rw-r--r-- 1 root root 29784 2011-01-12 11:41 kernel.img
-rw-r--r-- 1 root root  2092 2011-01-12 11:41 keystatus.mod
-rw-r--r-- 1 root root  5056 2011-01-12 11:41 linux16.mod
-rw-r--r-- 1 root root  8740 2011-01-12 11:41 linux.mod
-rw-r--r-- 1 root root  1024 2011-01-12 11:41 lnxboot.img
-rw-r--r-- 1 root root  5632 2011-01-12 11:41 loadenv.mod
drwxr-xr-x 2 root root  4096 2011-01-12 11:41 locale
-rw-r--r-- 1 root root  3168 2011-01-12 11:41 loopback.mod
-rw-r--r-- 1 root root  1388 2011-01-12 11:41 lsmmap.mod
-rw-r--r-- 1 root root  4224 2011-01-12 11:41 ls.mod
-rw-r--r-- 1 root root  5032 2011-01-12 11:41 lspci.mod
-rw-r--r-- 1 root root  5580 2011-01-12 11:41 lvm.mod
-rw-r--r-- 1 root root  1876 2011-01-12 11:41 mdraid.mod
-rw-r--r-- 1 root root  2192 2011-01-12 11:41 memdisk.mod
-rw-r--r-- 1 root root  2964 2011-01-12 11:41 memrw.mod
-rw-r--r-- 1 root root  4300 2011-01-12 11:41 minicmd.mod
-rw-r--r-- 1 root root  4384 2011-01-12 11:41 minix.mod
-rw-r--r-- 1 root root  8632 2011-01-12 11:41 mmap.mod
-rw-r--r-- 1 root root  2629 2011-01-12 11:41 moddep.lst
-rw-r--r-- 1 root root  2468 2011-01-12 11:41 msdospart.mod
-rw-r--r-- 1 root root 11268 2011-01-12 11:41 multiboot2.mod
-rw-r--r-- 1 root root 11264 2011-01-12 11:41 multiboot.mod
-rw-r--r-- 1 root root 42144 2011-01-12 11:41 normal.mod
-rw-r--r-- 1 root root  3640 2011-01-12 11:41 ntfscomp.mod
-rw-r--r-- 1 root root 10032 2011-01-12 11:41 ntfs.mod
-rw-r--r-- 1 root root  4572 2011-01-12 11:41 ohci.mod
-rw-r--r-- 1 root root  2180 2011-01-12 11:41 part_acorn.mod
-rw-r--r-- 1 root root  2284 2011-01-12 11:41 part_amiga.mod
-rw-r--r-- 1 root root  2724 2011-01-12 11:41 part_apple.mod
-rw-r--r-- 1 root root  2824 2011-01-12 11:41 part_gpt.mod
-rw-r--r-- 1 root root    62 2011-01-12 11:41 partmap.lst
-rw-r--r-- 1 root root  3540 2011-01-12 11:41 part_msdos.mod
-rw-r--r-- 1 root root  2408 2011-01-12 11:41 part_sun.mod
-rw-r--r-- 1 root root    22 2011-01-12 11:41 parttool.lst
-rw-r--r-- 1 root root  4572 2011-01-12 11:41 parttool.mod
-rw-r--r-- 1 root root  2000 2011-01-12 11:41 password.mod
-rw-r--r-- 1 root root  3104 2011-01-12 11:41 password_pbkdf2.mod
-rw-r--r-- 1 root root  1420 2011-01-12 11:41 pbkdf2.mod
-rw-r--r-- 1 root root   980 2011-01-12 11:41 pci.mod
-rw-r--r-- 1 root root  2580 2011-01-12 11:41 play.mod
-rw-r--r-- 1 root root  6736 2011-01-12 11:41 png.mod
-rw-r--r-- 1 root root  2752 2011-01-12 11:41 probe.mod
-rw-r--r-- 1 root root  1024 2011-01-12 11:41 pxeboot.img
-rw-r--r-- 1 root root  1420 2011-01-12 11:41 pxecmd.mod
-rw-r--r-- 1 root root  5632 2011-01-12 11:41 pxe.mod
-rw-r--r-- 1 root root  1472 2011-01-12 11:41 raid5rec.mod
-rw-r--r-- 1 root root  2920 2011-01-12 11:41 raid6rec.mod
-rw-r--r-- 1 root root  5940 2011-01-12 11:41 raid.mod
-rw-r--r-- 1 root root  1628 2011-01-12 11:41 read.mod
-rw-r--r-- 1 root root  1212 2011-01-12 11:41 reboot.mod
-rw-r--r-- 1 root root  9924 2011-01-12 11:41 reiserfs.mod
-rw-r--r-- 1 root root  4240 2011-01-12 11:41 relocator.mod
-rw-r--r-- 1 root root  3344 2011-01-12 11:41 scsi.mod
-rw-r--r-- 1 root root  2260 2011-01-12 11:41 search_fs_file.mod
-rw-r--r-- 1 root root  2408 2011-01-12 11:41 search_fs_uuid.mod
-rw-r--r-- 1 root root  2356 2011-01-12 11:41 search_label.mod
-rw-r--r-- 1 root root  2444 2011-01-12 11:41 search.mod
-rw-r--r-- 1 root root  6180 2011-01-12 11:41 serial.mod
-rw-r--r-- 1 root root   778 2011-01-12 11:41 setjmp.mod
-rw-r--r-- 1 root root  5620 2011-01-12 11:41 setpci.mod
-rw-r--r-- 1 root root  4140 2011-01-12 11:41 sfs.mod
-rw-r--r-- 1 root root 12208 2011-01-12 11:41 sh.mod
-rw-r--r-- 1 root root  2304 2011-01-12 11:41 sleep.mod
-rw-r--r-- 1 root root  2920 2011-01-12 11:41 tar.mod
-rw-r--r-- 1 root root   134 2011-01-12 11:41 terminal.lst
-rw-r--r-- 1 root root  5108 2011-01-12 11:41 terminal.mod
-rw-r--r-- 1 root root  9848 2011-01-12 11:41 terminfo.mod
-rw-r--r-- 1 root root  5240 2011-01-12 11:41 test.mod
-rw-r--r-- 1 root root  2996 2011-01-12 11:41 tga.mod
-rw-r--r-- 1 root root  1763 2011-01-12 11:41 trig.mod
-rw-r--r-- 1 root root  1360 2011-01-12 11:41 true.mod
-rw-r--r-- 1 root root  5144 2011-01-12 11:41 udf.mod
-rw-r--r-- 1 root root  4720 2011-01-12 11:41 ufs1.mod
-rw-r--r-- 1 root root  5036 2011-01-12 11:41 ufs2.mod
-rw-r--r-- 1 root root  5268 2011-01-12 11:41 uhci.mod
-rw-r--r-- 1 root root  3516 2011-01-12 11:41 usb_keyboard.mod
-rw-r--r-- 1 root root  3916 2011-01-12 11:41 usb.mod
-rw-r--r-- 1 root root  3904 2011-01-12 11:41 usbms.mod
-rw-r--r-- 1 root root  3572 2011-01-12 11:41 usbtest.mod
-rw-r--r-- 1 root root  2820 2011-01-12 11:41 vbeinfo.mod
-rw-r--r-- 1 root root  7996 2011-01-12 11:41 vbe.mod
-rw-r--r-- 1 root root  3136 2011-01-12 11:41 vbetest.mod
-rw-r--r-- 1 root root  3888 2011-01-12 11:41 vga.mod
-rw-r--r-- 1 root root  2912 2011-01-12 11:41 vga_text.mod
-rw-r--r-- 1 root root 17260 2011-01-12 11:41 video_fb.mod
-rw-r--r-- 1 root root     4 2011-01-12 11:41 video.lst
-rw-r--r-- 1 root root  5692 2011-01-12 11:41 video.mod
-rw-r--r-- 1 root root  3920 2011-01-12 11:41 videotest.mod
-rw-r--r-- 1 root root  5876 2011-01-12 11:41 xfs.mod
-rw-r--r-- 1 root root 31428 2011-01-12 11:41 xnu.mod
-rw-r--r-- 1 root root  2028 2011-01-12 11:41 xnu_uuid.mod
-rw-r--r-- 1 root root  6292 2011-01-12 11:41 zfsinfo.mod
-rw-r--r-- 1 root root 24164 2011-01-12 11:41 zfs.mod

Is this normal..i didn't remember or else understand why i have this one  in my home partition.I maybe understand that this files are somekind of  settting or something a system needed as you can observe it from its  filename.

Hope you can clarify me about all of this files

Or should i delete this directory..

I already check my /boot/grub/* in my main root partition.

---

### Post by deconstrained on 2011-02-22
No, this is definitely not normal. You have cause for concern.

See what's going on:
```
df -h
cat /etc/fstab
```

---


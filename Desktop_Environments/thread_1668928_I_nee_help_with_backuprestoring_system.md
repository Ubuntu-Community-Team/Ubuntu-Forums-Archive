---
title: "I nee help with backup/restoring system"
date: 2011-01-17
forum: Desktop Environments
---

### Post by throese on 2011-01-17
I followed the instructions here: [http://ubuntuforums.org/showthread.php?t=35087&highlight=System+Restore](http://ubuntuforums.org/showthread.php?t=35087&highlight=System+Restore) to back up my system a few months back.

I still have the backup.tar.tgz file on my external hard drive. But my problem is the restoring part. Well, yesterday I did the tar xvpfz backup.tgz -C / command and it unpacked everything and put it back to the way it was (based on my backup file).

I had all of my programs again (note now that his was a FRESH install of Ubuntu BEFORE I unpacked the file) and what not. Now, I was able to do w/e I want.

Here's the problem:

Every time I restart my laptop, I'd always get this CLI that says some kind of error and give me something like this:

(inidect) type "help" for more information/commands or something like that and I would never know what to do except for re-installing Ubuntu and waiting till 2 AM to re-download all the updates and stuff.

So, what can I do so the above stops happening and I can use my revived system without having to worry about it messing up and having to re-install my OS and all the updates every single time. I'm tired of it and I can't think of any other way as to how I can back up my laptop. Remastersys only goes up to 12 GB and I don't know how to use CloneZilla.

---

### Post by wilee-nilee on 2011-01-17
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

This will give a what is where of the system.

Does the cli you see look like this--->   grub>

---

### Post by throese on 2011-01-17
No, it does not look like that. I'll DL a VB system and show you what it looks like that way.

Additional Question: Why is it that when once you DL a .deb package and install it, that if you copy/paste the .deb package onto a flash drive and uninstall the program for w/e reason that if you try to use the .deb package again, it won't let you for w/e reason?

---

### Post by wilee-nilee on 2011-01-17
> **throese said:**
> No, it does not look like that. I'll DL a VB system and show you what it looks like that way.

Don't waste your time for me all I wanted was the bootscript, I don't like where this is heading already, we are not on the same page.

---

### Post by throese on 2011-01-17
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   224,827,391   224,825,344  83 Linux
/dev/sda2         224,829,438   234,440,703     9,611,266   5 Extended
/dev/sda5         224,829,440   234,440,703     9,611,264  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        49faae21-ae07-4e81-b258-ea4d8ace48ac   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        e725c5ed-6f64-40f6-a3a7-086d290061c5   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb         5ACC-A0A7                              vfat       KINGSTON16                    

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb         /media/KINGSTON16        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 49faae21-ae07-4e81-b258-ea4d8ace48ac
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 49faae21-ae07-4e81-b258-ea4d8ace48ac
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 49faae21-ae07-4e81-b258-ea4d8ace48ac
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=49faae21-ae07-4e81-b258-ea4d8ace48ac ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 49faae21-ae07-4e81-b258-ea4d8ace48ac
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=49faae21-ae07-4e81-b258-ea4d8ace48ac ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 49faae21-ae07-4e81-b258-ea4d8ace48ac
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=49faae21-ae07-4e81-b258-ea4d8ace48ac ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 49faae21-ae07-4e81-b258-ea4d8ace48ac
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=49faae21-ae07-4e81-b258-ea4d8ace48ac ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 49faae21-ae07-4e81-b258-ea4d8ace48ac
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 49faae21-ae07-4e81-b258-ea4d8ace48ac
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=49faae21-ae07-4e81-b258-ea4d8ace48ac /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e725c5ed-6f64-40f6-a3a7-086d290061c5 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  86.0GB: boot/grub/core.img
    .1GB: boot/grub/grub.cfg
  69.0GB: boot/initrd.img-2.6.32-21-generic
  86.1GB: boot/initrd.img-2.6.32-27-generic
  86.0GB: boot/vmlinuz-2.6.32-21-generic
  86.1GB: boot/vmlinuz-2.6.32-27-generic
  86.1GB: initrd.img
  69.0GB: initrd.img.old
  86.1GB: vmlinuz
  86.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  c3 1d c9 eb d5 fc 30 da  01 05 a3 e8 32 0a 85 00  |......0.....2...|
00000010  ff 46 ae c4 85 03 a0 9d  b4 d3 33 60 a3 2b 54 61  |.F........3`.+Ta|
00000020  2d 5c 7a e7 e4 5e 9e a8  76 d0 97 9b f7 4f 58 58  |-\z..^..v....OXX|
00000030  8d 23 c7 e6 3d 06 63 9f  f1 ec 18 b9 fb 56 01 c8  |.#..=.c......V..|
00000040  fd 2e 94 71 3f 0c 32 36  6a 16 c1 f7 e1 8f 38 ba  |...q?.26j.....8.|
00000050  dc e5 50 18 1c b2 77 4e  86 98 d6 7b 55 3f be a5  |..P...wN...{U?..|
00000060  48 3d 01 fd b1 ed 9e 1e  ae f7 a6 b2 bd fb 29 bc  |H=............).|
00000070  7d 4d 49 95 c0 21 ad fc  88 fb f2 c0 5e 92 ec 9f  |}MI..!......^...|
00000080  8d 7c cd f1 bb bf 58 54  3b 53 c0 d7 73 d5 81 97  |.|....XT;S..s...|
00000090  6d 28 17 3b 32 e1 a0 5e  21 93 87 b9 b9 2c 1b 7e  |m(.;2..^!....,.~|
000000a0  3d 52 9f 55 ef ef 72 73  53 1b ec 77 dc 93 98 87  |=R.U..rsS..w....|
000000b0  f3 99 73 14 5f 3a 6d 76  8f 56 4d 7a 71 b9 f4 9b  |..s._:mv.VMzq...|
000000c0  92 5b 76 00 e2 0b 33 c0  c6 97 c2 aa b3 ad 30 56  |.[v...3.......0V|
000000d0  cb 80 04 b3 d8 18 72 c6  13 a3 a7 96 29 72 8e de  |......r.....)r..|
000000e0  be c9 41 7c 1a 69 50 78  25 d1 87 d1 75 1c f3 94  |..A|.iPx%...u...|
000000f0  34 e6 ca 2a 7b c8 cb 98  45 ba 4b ba 53 02 c9 1f  |4..*{...E.K.S...|
00000100  ff a2 90 a0 c5 d0 75 cd  d1 ae 7c 49 bf dc 42 dc  |......u...|I..B.|
00000110  dc fc d9 31 bb 67 37 8d  88 85 57 15 f5 01 b1 50  |...1.g7...W....P|
00000120  fb bc 0a b7 3e 6d f4 af  4d ee dd c5 a0 dd 1e cf  |....>m..M.......|
00000130  3c ad ec de b1 ee 8c 0d  4b d4 9c 8e 86 d1 f8 1b  |<.......K.......|
00000140  de dc 57 c9 3c db 3a 07  99 ca e7 2d 1c 80 2e 4b  |..W.<.:....-...K|
00000150  9a e7 b1 b6 d9 e4 2e 18  cb f6 e7 0d f8 c0 e4 e7  |................|
00000160  fc 2c 51 d7 34 5a 36 e9  69 1a 20 68 dd eb 03 ef  |.,Q.4Z6.i. h....|
00000170  c9 bc f0 2a 21 64 df a2  59 d0 7c 8f 4f 26 df 6f  |...*!d..Y.|.O&.o|
00000180  80 b0 1e 3e f1 91 70 e4  aa e7 cf b8 c5 38 fa 23  |...>..p......8.#|
00000190  21 00 25 c6 4c 2b 3c 1d  bd 9d 0f d9 d4 d2 c0 ef  |!.%.L+<.........|
000001a0  9c f2 24 f5 fd ea 97 1a  f0 f6 cb b4 b7 ed a8 b4  |..$.............|
000001b0  4d 9a dc 12 26 9e a0 a7  67 a8 1f 13 17 da 00 fe  |M...&...g.......|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a8 92 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by throese on 2011-01-17
Here is what I was talking about, this is what I get once I've done the ```
tar xvpzf backup.tgz -C /
```:

So what do I do from here? I did it all in Oracle Virtual Box 4.0

---


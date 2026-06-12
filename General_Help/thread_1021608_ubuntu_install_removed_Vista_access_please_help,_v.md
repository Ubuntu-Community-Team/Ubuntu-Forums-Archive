---
title: "ubuntu install removed Vista access? please help, very confused, freak out imminent."
date: 2008-12-25
forum: General Help
---

### Post by Nitonale on 2008-12-25
&#65279;I am new to Linux and Ubuntu, but I usually pick up on things fast, so please bear with me. 

My laptop is an HP Pavilion dv6000. My normal OS is 64bit Windows Vista. I've always wanted to try out Linux, but I didn't want to partition my laptop's hard drive, so I was very happy when I read that you could install it onto a flash drive from a live CD. 

Here's what happened, in a nice list format. 

- I downloaded the 64bit Unbuntu 8.10 ISO and burned it to disk. 
- I restarted my computer and booted from the live cd. 
- I put in my flash drive and first tried the "create a usb start up disk" option. This failed and the window crashed. 
- I then tried the first tutorial found here. [Link.]("http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/") 
- This seemed to work just fine, but I wanted to make sure. I shut down my computer and rebooted without the flash drive or the disk. Instead of the usual Vista logo popping up, I got this message, which I'm guessing is the startup message for Ubuntu. > SYSLINUX 3.63 Debian-2008-07-15 EBIOS Copyright (c) 1994-2008 H. Peter Anvin 

- When this happened, I inserted the flash drive. Nothing happened. I inserted the disk as well, and this time Ubuntu booted up again. 
- Trying to figure out what happened, I restarted my computer once again, this time without the USB stick or the disk. 
- I went into BIOS and into system set up to change the boot order and figure out how to run Vista, but nothing worked. I repeatedly got the above quoted message. 

I have a few questions. 

How do I resume using Vista? 
Have I done something stupid and removed access to my hard drive? 
If so, is there a way I can recover my data? 


Please help in any way that you possibly can. Thank you very much. 


Update: 

> **caljohnsmith said:**
> Yikes, I hate to break the news, but there is no sign of Vista on your sda 250 GB drive. You have one FAT and one Linux partition on that drive now. If you had some really important files in Vista that you want to recover, you could try [photorec]("http://www.cgsecurity.org/wiki/PhotoRec"). Really sorry about your loss though.

I have recovery disks. Will this so anything, or do I have to start from scratch?

---

### Post by caljohnsmith on 2008-12-25
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what your problem might be.

---

### Post by ajcham on 2008-12-25
I've just had a look at the script you ran to install to the pendrive.  When you were prompted *"What is your drive letter?:"*, what did you enter? Did you confirm that this was the correct letter for your USB drive?

Because, if I were to hazard a guess, I would suggest you may have actually given the letter corresponding to your HD, which would have wiped Vista.  I hope I'm wrong.

Try booting the Live disk again and run:
```
sudo fdisk -l
``` and post the results here.[-o<

---

### Post by Nitonale on 2008-12-25
Here you go, hope it helps. 

> ========================== Boot Info Summary: ===========================

Gateway? is installed in the MBR of /dev/sda
========================== Boot Info Summary: ===========================

No known boot loader is installed in the MBR of /dev/sdb

sda1:
    File system:  vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts at sector 63.
    Operating System:  
    Boot files/directories present: 

sda2:
    File system:  ext2
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/directories present: 

========================== "fdisk -lu" output: ==========================

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x55a255a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   195366464    97683201    c  W95 FAT32 (LBA)
/dev/sda2       195366465   390716864    97675200   83  Linux

========================== "sfdisk -V" output: ==========================

/dev/sda: OK

========================== "fdisk -lu" output: ==========================

Disk /dev/sdb: 2045 MB, 2045247488 bytes
63 heads, 62 sectors/track, 1022 cylinders, total 3994624 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?   778135908  1919645538   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(199215, 34, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(491460, 44, 51)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?   168689522  2104717761   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(43187, 17, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(538842, 14, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?  1869881465  3805909656   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(478720, 18, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(974375, 14, 39)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?           0  3637226495  1818613248    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(931189, 36, 30)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

========================== "sfdisk -V" output: ==========================

/dev/sda: OK
Warning: partitions 1 and 2 overlap

===================== "blkid -c /dev/null" output: ======================

/dev/sda1: LABEL="ubuntu8" UUID="4954-0042" TYPE="vfat" 
/dev/sda2: LABEL="casper-rw" UUID="4db8acb8-1316-42fa-86bd-a44adc061476" TYPE="ext2" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb: SEC_TYPE="msdos" LABEL="UNBUNTU" UUID="D097-9B3D" TYPE="vfat" 

============================ "mount" output: ============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb on /media/UNBUNTU type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)

============================ StdErr Messages: ============================

Unknown MBR on /dev/sdb

00000000  eb 3c 90 4d 53 44 4f 53  35 2e 30 00 02 40 08 00  |.<.MSDOS5.0..@..|
00000010  02 00 02 00 00 f8 f4 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 f4 3c 00 80 00 29 3d  9b 97 d0 4e 4f 20 4e 41  |..<...)=...NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 33 c9  |ME    FAT16   3.|
00000040  8e d1 bc f0 7b 8e d9 b8  00 20 8e c0 fc bd 00 7c  |....{.... .....||
00000050  38 4e 24 7d 24 8b c1 99  e8 3c 01 72 1c 83 eb 3a  |8N$}$....<.r...:|
00000060  66 a1 1c 7c 26 66 3b 07  26 8a 57 fc 75 06 80 ca  |f..|&f;.&.W.u...|
00000070  02 88 56 02 80 c3 10 73  eb 33 c9 8a 46 10 98 f7  |..V....s.3..F...|
00000080  66 16 03 46 1c 13 56 1e  03 46 0e 13 d1 8b 76 11  |f..F..V..F....v.|
00000090  60 89 46 fc 89 56 fe b8  20 00 f7 e6 8b 5e 0b 03  |`.F..V.. ....^..|
000000a0  c3 48 f7 f3 01 46 fc 11  4e fe 61 bf 00 00 e8 e6  |.H...F..N.a.....|
000000b0  00 72 39 26 38 2d 74 17  60 b1 0b be a1 7d f3 a6  |.r9&8-t.`....}..|
000000c0  61 74 32 4e 74 09 83 c7  20 3b fb 72 e6 eb dc a0  |at2Nt... ;.r....|
000000d0  fb 7d b4 7d 8b f0 ac 98  40 74 0c 48 74 13 b4 0e  |.}.}....@t.Ht...|
000000e0  bb 07 00 cd 10 eb ef a0  fd 7d eb e6 a0 fc 7d eb  |.........}....}.|
000000f0  e1 cd 16 cd 19 26 8b 55  1a 52 b0 01 bb 00 00 e8  |.....&.U.R......|
00000100  3b 00 72 e8 5b 8a 56 24  be 0b 7c 8b fc c7 46 f0  |;.r.[.V$..|...F.|
00000110  3d 7d c7 46 f4 29 7d 8c  d9 89 4e f2 89 4e f6 c6  |=}.F.)}...N..N..|
00000120  06 96 7d cb ea 03 00 00  20 0f b6 c8 66 8b 46 f8  |..}..... ...f.F.|
00000130  66 03 46 1c 66 8b d0 66  c1 ea 10 eb 5e 0f b6 c8  |f.F.f..f....^...|
00000140  4a 4a 8a 46 0d 32 e4 f7  e2 03 46 fc 13 56 fe eb  |JJ.F.2....F..V..|
00000150  4a 52 50 06 53 6a 01 6a  10 91 8b 46 18 96 92 33  |JRP.Sj.j...F...3|
00000160  d2 f7 f6 91 f7 f6 42 87  ca f7 76 1a 8a f2 8a e8  |......B...v.....|
00000170  c0 cc 02 0a cc b8 01 02  80 7e 02 0e 75 04 b4 42  |.........~..u..B|
00000180  8b f4 8a 56 24 cd 13 61  61 72 0b 40 75 01 42 03  |...V$..aar.@u.B.|
00000190  5e 0b 49 75 06 f8 c3 41  bb 00 00 60 66 6a 00 eb  |^.Iu...A...`fj..|
000001a0  b0 42 4f 4f 54 4d 47 52  20 20 20 20 0d 0a 52 65  |.BOOTMGR    ..Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 00 00 ac cb d8 55 aa  |rt............U.|
00000200


---

### Post by Nitonale on 2008-12-25
> **ajcham said:**
> I've just had a look at the script you ran to install to the pendrive.  When you were prompted *"What is your drive letter?:"*, what did you enter? Did you confirm that this was the correct letter for your USB drive?

Because, if I were to hazard a guess, I would suggest you may have actually given the letter corresponding to your HD, which would have wiped Vista.  I hope I'm wrong.

Try booting the Live disk again and run:
```
sudo fdisk -l
``` and post the results here.[-o<

Oh crap. I checked, but I could be wrong. *crosses fingers* 

> Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x55a255a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12161    97683201    c  W95 FAT32 (LBA)
/dev/sda2           12162       24321    97675200   83  Linux

Disk /dev/sdb: 2045 MB, 2045247488 bytes
63 heads, 62 sectors/track, 1022 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      199216      491461   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(199215, 34, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(491460, 44, 51)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       43188      538843   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(43187, 17, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(538842, 14, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      478721      974376   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(478720, 18, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(974375, 14, 39)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?           1      931190  1818613248    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(931189, 36, 30)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order


---

### Post by caljohnsmith on 2008-12-25
Yikes, I hate to break the news, but there is no sign of Vista on your sda 250 GB drive. You have one FAT and one Linux partition on that drive now. If you had some really important files in Vista that you want to recover, you could try [photorec]("http://www.cgsecurity.org/wiki/PhotoRec"). Really sorry about your loss though.

---

### Post by Aearenda on 2008-12-25
Edit - I was a bit slow typing this (I got distracted), and this response was out of date, so I removed it.

---

### Post by Nitonale on 2008-12-25
> **caljohnsmith said:**
> Yikes, I hate to break the news, but there is no sign of Vista on your sda 250 GB drive. You have one FAT and one Linux partition on that drive now. If you had some really important files in Vista that you want to recover, you could try [photorec]("http://www.cgsecurity.org/wiki/PhotoRec"). Really sorry about your loss though.

Holy crap. Thanks for the help, I'll try photorec. 

New question: I have recovery disks. Can I somehow use these to fix this or is there no chance?

---

### Post by Nitonale on 2008-12-25
> **Aearenda said:**
> I suspect you've allowed Ubuntu to overwrite the Master Boot Record on the main hard drive, and it will therefore not boot without the flash drive being present. To fix this on XP, you boot from the installation CD, go into recovery mode and use FixMBR to put it back. But I've never used Vista, thanks to Ubuntu, so you'll have to google how to fix the MBR for Vista!

Edit - I was a bit slow typing this (I got distracted), and this response is now out of date.

I will look into this, thank you.

---

### Post by ajcham on 2008-12-25
Bad news I'm afraid, it looks very much like the script has gone to work on your HD rather than the flash drive:

> ```
Device Boot Start End Blocks Id System
/dev/sda1 * 1 12161 97683201 c W95 FAT32 (LBA)
/dev/sda2 12162 24321 97675200 83 Linux
```

This is exactly how the script is supposed to format the USB drive, two equally sized partitions - FAT32 and Ext.

I hope you've not lost anything too important.

---

### Post by caljohnsmith on 2008-12-25
> **Nitonale said:**
> Holy crap. Thanks for the help, I'll try photorec. 

New question: I have recovery disks. Can I somehow use these to fix this or is there no chance?
You should be able to reinstall Vista from scratch with your recovery disks; but as far as trying to recover any important data that you might have had in Vista, that's going to be tough even with photorec, because you've definitely overwritten the Vista partition. And by the way, restoring a Windows MBR to the drive is unfortunately not going to help any at this point since Vista is now gone. Best of luck, and again, sorry things didn't go as planned for you.

---

### Post by Nitonale on 2008-12-25
I've got some of my stuff backed up in one way or another, but I have lost quite a few things. I'm angry at myself, but I suppose it could be worse. Just have to grin and bear it. Maybe go cry in a corner for awhile.

---

### Post by Nitonale on 2008-12-25
I suppose it's a good thing I like Ubuntu then, eh? XD

---

### Post by ajcham on 2008-12-25
> **Nitonale said:**
> I've got some of my stuff backed up in one way or another, but I have lost quite a few things. I'm angry at myself, but I suppose it could be worse. Just have to grin and bear it. Maybe go cry in a corner for awhile.
--------------------------------------------------------------
I suppose it's a good thing I like Ubuntu then, eh? XD 

Good to see you can still smile through it! Once you've got Vista back up and running, I hope you give it another go.

If you do decide to try the USB route again, this is the part of the process in which you need to be wary:
```
"Please locate your flash drive from the list of"
"devices displayed above and enter it's letter."

"For example, if your flash drive is /dev/sdx,"
"you would type x and then press Enter"

"What is your drive letter?:"
```

Make sure to use the correct letter! Good luck.

---


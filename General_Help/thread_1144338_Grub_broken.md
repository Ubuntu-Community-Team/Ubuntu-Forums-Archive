---
title: "Grub broken"
date: 2009-04-30
forum: General Help
---

### Post by EvanKroske on 2009-04-30
That's right, I've somehow managed to break grub, so now in addition to having a non-functioning jaunty installation, I also can't use my windows installation. I tried to follow the instructions under "Recover Grub" [here]("https://help.ubuntu.com/community/LiveCdRecovery"), but I get an error 15 when I try to find /boot/grub/stage1 or /grub/stage1. Even if you can't tell me what's wrong or how to fix it, I would appreciate any links about grub you think might be helpful. Thanks.

---

### Post by nandemonai on 2009-04-30
Try this one:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by codeseer on 2009-04-30
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

```

cd whereveryoudownloaditto
sudo ./boot*.sh

```

Post Results.txt content inside CODE (#) blocks here.

---

### Post by codeseer on 2009-04-30
Edit: sorry about double-post. Firefox crashed when I hit the submit button. :/

---

### Post by EvanKroske on 2009-04-30
Uh-oh. When I try to run your script, I get ```
./boot_info_script032.sh: command not found
```Is there another version I should use?

---

### Post by codeseer on 2009-04-30
> **EvanKroske said:**
> Uh-oh. When I try to run your script, I get ```
./boot_info_script032.sh: command not found
```Is there another version I should use?

Make it executable.

```
chmod +x boot*.sh
```

...or just set the permissions in the right-click properties.

---

### Post by EvanKroske on 2009-04-30
Okay, here's the whole output:
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => HP/Gateway is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   955,979,954   955,979,892   7 HPFS/NTFS
/dev/sda3         955,979,955   976,768,064    20,788,110   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x42723102

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   953,007,929   953,007,867  83 Linux
/dev/sdb2         953,007,930   976,768,064    23,760,135   5 Extended
/dev/sdb5         953,007,993   976,768,064    23,760,072  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1037 MB, 1037041152 bytes
4 heads, 8 sectors/track, 63295 cylinders, total 2025471 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *              8     2,025,470     2,025,463   e W95 FAT16 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="FCBAC87BBAC833C4" LABEL="HP" TYPE="ntfs" 
/dev/sda3: UUID="949CA48C9CA46A86" LABEL="FACTORY_IMAGE" TYPE="ntfs" 
/dev/sdb1: UUID="b01f7b95-3de9-478d-8a56-c3b353e92c59" TYPE="ext3" 
/dev/sdb5: UUID="7bc6fb5b-5109-4af8-84b6-abf2fe7415ed" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
/dev/sdc1: SEC_TYPE="msdos" UUID="02F4-030F" TYPE="vfat" 

=============================== "mount" output: ===============================

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
/dev/sdb1 on /mnt type ext3 (rw)
/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=b01f7b95-3de9-478d-8a56-c3b353e92c59 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=7bc6fb5b-5109-4af8-84b6-abf2fe7415ed none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


 289.6GB: boot/vmlinuz-2.6.27-7-generic
 289.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1

00000000  eb 3c 90 44 4f 4b 30 31  2e 30 32 00 02 20 01 00  |.<.DOK01.02.. ..|
00000010  02 00 02 00 00 f8 f8 00  08 00 04 00 08 00 00 00  |................|
00000020  f7 e7 1e 00 80 00 29 0f  03 f4 02 00 00 00 00 00  |......).........|
00000030  00 00 00 00 00 00 46 41  54 31 36 20 20 20 33 c9  |......FAT16   3.|
00000040  8e d1 bc fc 7b 16 07 bd  78 00 c5 76 00 1e 56 16  |....{...x..v..V.|
00000050  55 bf 22 05 89 7e 00 89  4e 02 b1 0b fc f3 a4 06  |U."..~..N.......|
00000060  1f bd 00 7c c6 45 fe 0f  38 4e 24 7d 20 8b c1 99  |...|.E..8N$} ...|
00000070  e8 7e 01 83 eb 3a 66 a1  1c 7c 66 3b 07 8a 57 fc  |.~...:f..|f;..W.|
00000080  75 06 80 ca 02 88 56 02  80 c3 10 73 ed 33 c9 fe  |u.....V....s.3..|
00000090  06 d8 7d 8a 46 10 98 f7  66 16 03 46 1c 13 56 1e  |..}.F...f..F..V.|
000000a0  03 46 0e 13 d1 8b 76 11  60 89 46 fc 89 56 fe b8  |.F....v.`.F..V..|
000000b0  20 00 f7 e6 8b 5e 0b 03  c3 48 f7 f3 01 46 fc 11  | ....^...H...F..|
000000c0  4e fe 61 bf 00 07 e8 28  01 72 3e 38 2d 74 17 60  |N.a....(.r>8-t.`|
000000d0  b1 0b be d8 7d f3 a6 61  74 3d 4e 74 09 83 c7 20  |....}..at=Nt... |
000000e0  3b fb 72 e7 eb dd fe 0e  d8 7d 7b a7 be 7f 7d ac  |;.r......}{...}.|
000000f0  98 03 f0 ac 98 40 74 0c  48 74 13 b4 0e bb 07 00  |.....@t.Ht......|
00000100  cd 10 eb ef be 82 7d eb  e6 be 80 7d eb e1 cd 16  |......}....}....|
00000110  5e 1f 66 8f 04 cd 19 be  81 7d 8b 7d 1a 8d 45 fe  |^.f......}.}..E.|
00000120  8a 4e 0d f7 e1 03 46 fc  13 56 fe b1 04 e8 c2 00  |.N....F..V......|
00000130  72 d7 ea 00 02 70 00 52  50 06 53 6a 01 6a 10 91  |r....p.RP.Sj.j..|
00000140  8b 46 18 a2 26 05 96 92  33 d2 f7 f6 91 f7 f6 42  |.F..&...3......B|
00000150  87 ca f7 76 1a 8a f2 8a  e8 c0 cc 02 0a cc b8 01  |...v............|
00000160  02 80 7e 02 0e 75 04 b4  42 8b f4 8a 56 24 cd 13  |..~..u..B...V$..|
00000170  61 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |aar.@u.B.^.Iuw..|
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 73 79 73  |..'..Invalid sys|
00000190  74 65 6d 20 64 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem disk...Disk |
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
000001c0  64 20 74 68 65 6e 20 70  72 65 73 73 20 61 6e 79  |d then press any|
000001d0  20 6b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | key....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|
000001f0  00 41 bb 00 07 60 66 6a  00 e9 3b ff 00 00 55 aa  |.A...`fj..;...U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 

```

---

### Post by codeseer on 2009-04-30
You need to issue a grub install to sdb1.

---

### Post by lindsay7 on 2009-04-30
Looks like you need to resetup your grub file first and that well bet you into Ubuntu. You may also need to reset the windows mbr and or get the grub and the mbr to agree.  Look at this post it should help, the part about restoring your grub file.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

you may need to do the following for the mrb, see this post

[http://geniushackers.com/blog/2008/04/02/recover-windows-mbr-using-ubuntu-live-cd/](http://geniushackers.com/blog/2008/04/02/recover-windows-mbr-using-ubuntu-live-cd/)

---

### Post by codeseer on 2009-04-30
You'll need to fire up the Live CD and do something like this, depending on where your root directory for that drive is:

```
sudo grub-install --root-directory=**/mnt/root** /dev/sdb1 --recheck
```

---

### Post by EvanKroske on 2009-04-30
Okay, I think it worked properly; below is the output. I'm going to try rebooting now, to see if windows boots properly or not.
```

Probing devices to guess BIOS drives. This may take a long time.
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /mnt/boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/mnt/boot/grub"] is not on an XFS filesystem
Installing GRUB to /dev/sdb1 as (hd1,0)...
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

```
Thanks for all the help guys; my computer would've been bricked without you.

---

### Post by codeseer on 2009-04-30
lol :) Hopefully it does.

---

### Post by EvanKroske on 2009-04-30
Success! Grub can now properly load windows (and probably linux, too.) However, I don't really want to type in grub commands every time I boot up my computer. Does anybody know how to get back the semi-GUI that lists all the OSs you have available and lets you pick which one you want to boot? A link would be just as helpful as a post (as long as it isn't to LetMeGoogleThatForYou.com :)) Thanks again!

---

### Post by codeseer on 2009-04-30
The first 5 steps of this will probably do you:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Sounds like your menu.lst is missing.

---

### Post by EvanKroske on 2009-05-01
Apparently I spoke too soon; Linux isn't booting. I've started a [new thread]("http://ubuntuforums.org/showthread.php?p=7190979") in the appropriate board to reflect the new problem. Thanks for helping me get grub working again.

---


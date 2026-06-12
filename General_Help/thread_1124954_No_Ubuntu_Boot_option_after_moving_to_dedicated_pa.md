---
title: "No Ubuntu Boot option after moving to dedicated partition."
date: 2009-04-13
forum: General Help
---

### Post by RonPDX on 2009-04-13
Good evening everyone. 

Earlier I moved my Wubi install to a dedicated partition. Everything appeared to go well after LVPM finished so I deleted my Wubi install and now I don't have the option of booting into Ubuntu. 

Before I go completely insane, does anyone have any idea's where I can start?

Ron 

p.s. I was have a problem with LVPM (Posted on the thread in the Tutorials section) that appears to have corrected itself after letting it run for a while.

---

### Post by meierfra. on 2009-04-13
In order to get a clearer picture of your setup, I suggest to from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by RonPDX on 2009-04-13
Meierfra -- Thank you so much for your quick response, below you will find the ressults. 

While in Windoze I took a quick look at the boot.ini file, shouldn't my default be /boot/grub/menu.lst /etc/fstab since I am no longer using Wubi? 

```
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3c162f0d

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325   263,112,569   263,032,245   7 HPFS/NTFS
/dev/sda3         263,112,570   478,158,659   215,046,090  83 Linux
/dev/sda4         478,158,660   488,392,064    10,233,405  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9dc96e9e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63        80,324        80,262  de Dell Utility
/dev/sdb2    *         80,325    78,108,029    78,027,705   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D4-0510" TYPE="vfat" 
/dev/sda2: UUID="7810A6D410A69920" LABEL="DRV2_VOL2" TYPE="ntfs" 
/dev/sda3: UUID="aeef767d-f564-4af7-9ce6-d75940125fb7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="fc8de1d1-4ebb-45b3-bf3c-84475db0e390" TYPE="swap" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D4-0510" TYPE="vfat" 
/dev/sdb2: UUID="0034491534490F5A" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)


================================ sda2/boot.ini: ================================

[boot loader]

timeout=15

default=c:\wubildr.mbr

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn


=========================== sda3/boot/grub/menu.lst: ===========================


# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title Windows
root (hd1,1)
makeactive
chainloader +1
boot


title Mythbuntu
root (hd0,1)
makeactive
chainloader +1
boot


=============================== sda3/etc/fstab: ===============================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sda3
UUID=aeef767d-f564-4af7-9ce6-d75940125fb7     /               ext3        defaults,errors=remount-ro    0   1
# /dev/sdb2
UUID=0034491534490F5A       /media/host0       ntfs-3g         defaults      0   0


# /dev/sda4
UUID=fc8de1d1-4ebb-45b3-bf3c-84475db0e390      none            swap        sw          0   0


=================== sda3: Location of files loaded by Grub: ===================


 200.4GB: boot/grub/menu.lst
 140.1GB: boot/initrd.img-2.6.27-12-generic
 140.1GB: boot/initrd.img-2.6.27-13-generic
 140.1GB: boot/initrd.img-2.6.27-14-generic
 140.2GB: boot/vmlinuz-2.6.27-12-generic
 140.2GB: boot/vmlinuz-2.6.27-13-generic
 140.2GB: boot/vmlinuz-2.6.27-14-generic
 140.1GB: initrd.img
 140.1GB: initrd.img.old
 140.2GB: vmlinuz
 140.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  0d 2f 16 3c 00 00 00 01  |........./.<....|
000001c0  01 00 de fe 3f 04 3f 00  00 00 86 39 01 00 80 00  |....?.?....9....|
000001d0  01 05 07 fe ff ff c5 39  01 00 b5 8d ad 0f 00 fe  |.......9........|
000001e0  ff ff 83 fe ff ff 7a c7  ae 0f ca 57 d1 0c 00 fe  |......z....W....|
000001f0  ff ff 82 fe ff ff 44 1f  80 1c 3d 26 9c 00 55 aa  |......D...=&..U.|
00000200



```

---

### Post by meierfra. on 2009-04-13
Something went wrong with the transfer. Grub did not get installed and menu.lst is missing all the  Ubuntu  entries.   Try this: Boot from the Ubuntu Live CD, open a terminal and type:

```
sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt --recheck /dev/sda
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt /bin/bash

```

and at the new prompt

```
update-grub
exit
```

Reboot, but set your bios to boot from the  250GB Ubuntu drive.

Your Windows entries on menu.lst still need some fixing. But we'll worry about that later.

---

### Post by RonPDX on 2009-04-13
Everything went well up until 

```
sudo chroot /mnt /bin/bash
```

```
chroot: cannot run command `/bin/bash': No such file or directory
```

---

### Post by meierfra. on 2009-04-13
Try 

```
sudo chroot /mnt
```

instead. If that does not work, post the output of

```
ls -l /mnt
```

---

### Post by RonPDX on 2009-04-13
That did not work as well, same result...

```
total 92
drwxr-xr-x   2 root root  4096 2009-04-13 19:32 bin
drwxrwxrwx   3 root root  4096 2009-04-13 19:32 boot
lrwxrwxrwx   1 root root    11 2009-04-13 19:32 cdrom -> media/cdrom
drwxr-xr-x  16 root root 14540 2009-04-13 19:58 dev
drwxr-xr-x 150 root root 12288 2009-04-13 23:39 etc
drwxr-xr-x   6 root root  4096 2009-04-13 19:33 home
drwxrwxrwx  37 root root  4096 2009-04-13 19:39 host
drwx------   2 root root  4096 2009-04-13 19:32 host2
lrwxrwxrwx   1 root root    33 2009-04-13 19:32 initrd.img -> boot/initrd.img-2.6.27-14-generic
lrwxrwxrwx   1 root root    33 2009-04-13 19:32 initrd.img.old -> boot/initrd.img-2.6.27-13-generic
drwxr-xr-x   2 root root  4096 2009-04-13 19:32 Ipod
drwx------   2 root root  4096 2009-04-13 19:32 lib
drwx------   2 root root 16384 2009-04-13 19:31 lost+found
drwx------   4 root root  4096 2009-04-13 23:39 media
drwx------   2 root root  4096 2009-04-13 19:32 mnt
drwx------   2 root root  4096 2009-04-13 19:32 opt
dr-xr-xr-x 112 root root     0 2009-04-13 19:57 proc
drwx------   2 root root  4096 2009-04-13 19:32 root
drwx------   2 root root  4096 2009-04-13 19:32 sbin
drwx------   2 root root  4096 2009-04-13 19:32 srv
drwxr-xr-x  12 root root     0 2009-04-13 19:57 sys
drwx------   2 root root  4096 2009-04-13 19:32 tmp
drwx------   2 root root  4096 2009-04-13 19:32 usr
drwx------   2 root root  4096 2009-04-13 19:32 var
lrwxrwxrwx   1 root root    30 2009-04-13 19:32 vmlinuz -> boot/vmlinuz-2.6.27-14-generic
lrwxrwxrwx   1 root root    30 2009-04-13 19:32 vmlinuz.old -> boot/vmlinuz-2.6.27-13-generic

```

---

### Post by meierfra. on 2009-04-13
One more output please

```
ls -l /mnt/bin
```

---

### Post by RonPDX on 2009-04-13
```
otal 6356
-rwxr-xr-x 1 root root  725136 2009-04-13 19:32 bash
-rwxr-xr-x 1 root root  127908 2009-04-13 19:32 bsd-csh
-rwxr-xr-x 1 root root   30140 2009-04-13 19:32 bunzip2
-rwxr-xr-x 1 root root   30140 2009-04-13 19:32 bzcat
lrwxrwxrwx 1 root root       6 2009-04-13 19:32 bzcmp -> bzdiff
-rwxr-xr-x 1 root root    2132 2009-04-13 19:32 bzdiff
lrwxrwxrwx 1 root root       6 2009-04-13 19:32 bzegrep -> bzgrep
-rwxr-xr-x 1 root root    4874 2009-04-13 19:32 bzexe
lrwxrwxrwx 1 root root       6 2009-04-13 19:32 bzfgrep -> bzgrep
-rwxr-xr-x 1 root root    3642 2009-04-13 19:32 bzgrep
-rwxr-xr-x 1 root root   30140 2009-04-13 19:32 bzip2
-rwxr-xr-x 1 root root    9524 2009-04-13 19:32 bzip2recover
lrwxrwxrwx 1 root root       6 2009-04-13 19:32 bzless -> bzmore
-rwxr-xr-x 1 root root    1297 2009-04-13 19:32 bzmore
-rwxr-xr-x 1 root root   30196 2009-04-13 19:32 cat
-rwxr-xr-x 1 root root   50784 2009-04-13 19:32 chgrp
-rwxr-xr-x 1 root root   46664 2009-04-13 19:32 chmod
-rwxr-xr-x 1 root root   50792 2009-04-13 19:32 chown
-rwxr-xr-x 1 root root    5472 2009-04-13 19:32 chvt
-rwxr-xr-x 1 root root   75492 2009-04-13 19:32 cp
-rwxr-xr-x 1 root root  118508 2009-04-13 19:32 cpio
lrwxrwxrwx 1 root root      21 2009-04-13 19:32 csh -> /etc/alternatives/csh
-rwxr-xr-x 1 root root   87924 2009-04-13 19:32 dash
-rwxr-xr-x 1 root root   58960 2009-04-13 19:32 date
-rwxr-xr-x 1 root root    9620 2009-04-13 19:32 dbus-cleanup-sockets
-rwxr-xr-x 1 root root  293268 2009-04-13 19:32 dbus-daemon
-rwxr-xr-x 1 root root    5476 2009-04-13 19:32 dbus-uuidgen
-rwxr-xr-x 1 root root   50820 2009-04-13 19:32 dd
-rwxr-xr-x 1 root root   50812 2009-04-13 19:32 df
-rwxr-xr-x 1 root root   96216 2009-04-13 19:32 dir
-rwxr-xr-x 1 root root    5468 2009-04-13 19:32 dmesg
-rwxr-xr-x 1 root root    9652 2009-04-13 19:32 dnsdomainname
-rwxr-xr-x 1 root root   57884 2009-04-13 19:32 dumpkeys
-rwxr-xr-x 1 root root   26048 2009-04-13 19:32 echo
-rwxr-xr-x 1 root root   40560 2009-04-13 19:32 ed
-rwxr-xr-x 1 root root   96216 2009-04-13 19:32 egrep
-rwxr-xr-x 1 root root   26036 2009-04-13 19:32 false
-rwxr-xr-x 1 root root    9576 2009-04-13 19:32 fgconsole
-rwxr-xr-x 1 root root   55156 2009-04-13 19:32 fgrep
-rwxr-xr-x 1 root root   22536 2009-04-13 19:32 fuser
-rwsr-xr-x 1 root root   22064 2009-04-13 19:32 fusermount
-rwxr-xr-x 1 root root  100312 2009-04-13 19:32 grep
-rwxr-xr-x 1 root root      63 2009-04-13 19:32 gunzip
-rwxr-xr-x 1 root root    5874 2009-04-13 19:32 gzexe
-rwxr-xr-x 1 root root   57360 2009-04-13 19:32 gzip
-rwxr-xr-x 1 root root    9648 2009-04-13 19:32 hostname
-rwxr-xr-x 1 root root  199468 2009-04-13 19:32 ip
-rwxr-xr-x 1 root root    9572 2009-04-13 19:32 kbd_mode
-rwxr-xr-x 1 root root   13748 2009-04-13 19:32 kill
-rwxr-xr-x 1 root root 1366136 2009-04-13 19:32 ld_static
-rwxr-xr-x 1 root root   42564 2009-04-13 19:32 ln
-rwxr-xr-x 1 root root   82676 2009-04-13 19:32 loadkeys
-rwxr-xr-x 1 root root   35080 2009-04-13 19:32 login
-rwxr-xr-x 1 root root   96216 2009-04-13 19:32 ls
-rwxr-xr-x 1 root root    5464 2009-04-13 19:32 lsmod
-rwxr-xr-x 1 root root   34312 2009-04-13 19:32 mkdir
-rwxr-xr-x 1 root root   30220 2009-04-13 19:32 mknod
-rwxr-xr-x 1 root root    9556 2009-04-13 19:32 mktemp
-rwxr-xr-x 1 root root   30316 2009-04-13 19:32 more
-rwsr-xr-x 1 root root   92584 2009-04-13 19:32 mount
-rwxr-xr-x 1 root root    5400 2009-04-13 19:32 mountpoint
lrwxrwxrwx 1 root root      20 2009-04-13 19:32 mt -> /etc/alternatives/mt
-rwxr-xr-x 1 root root   30604 2009-04-13 19:32 mt-gnu
-rwxr-xr-x 1 root root   83732 2009-04-13 19:32 mv
-rwxr-xr-x 1 root root  149420 2009-04-13 19:32 nano
lrwxrwxrwx 1 root root      20 2009-04-13 19:32 nc -> /etc/alternatives/nc
-rwxr-xr-x 1 root root   22076 2009-04-13 19:32 nc.traditional
lrwxrwxrwx 1 root root      24 2009-04-13 19:32 netcat -> /etc/alternatives/netcat
-rwxr-xr-x 1 root root  105068 2009-04-13 19:32 netstat
-rwxr-xr-x 1 root root   38796 2009-04-13 19:32 ntfs-3g
-rwxr-xr-x 1 root root    9580 2009-04-13 19:32 ntfs-3g.probe
lrwxrwxrwx 1 root root       6 2009-04-13 19:32 open -> openvt
-rwxr-xr-x 1 root root   13776 2009-04-13 19:32 openvt
lrwxrwxrwx 1 root root      16 2009-04-13 19:32 pidof -> ../sbin/killall5
-rwsr-xr-x 1 root root   30856 2009-04-13 19:32 ping
-rwsr-xr-x 1 root root   26684 2009-04-13 19:32 ping6
-rwxr-xr-x 1 root root   79636 2009-04-13 19:32 ps
-rwxr-xr-x 1 root root   30200 2009-04-13 19:32 pwd
lrwxrwxrwx 1 root root       4 2009-04-13 19:32 rbash -> bash
-rwxr-xr-x 1 root root   38452 2009-04-13 19:32 readlink
-rwxr-xr-x 1 root root   50744 2009-04-13 19:32 rm
-rwxr-xr-x 1 root root   26052 2009-04-13 19:32 rmdir
lrwxrwxrwx 1 root root       4 2009-04-13 19:32 rnano -> nano
-rwxr-xr-x 1 root root   13940 2009-04-13 19:32 run-parts
-rwxr-xr-x 1 root root   42900 2009-04-13 19:32 sed
-rwxr-xr-x 1 root root   34440 2009-04-13 19:32 setfont
-rwxr-xr-x 1 root root    8749 2009-04-13 19:32 setupcon
lrwxrwxrwx 1 root root       4 2009-04-13 19:32 sh -> dash
lrwxrwxrwx 1 root root       4 2009-04-13 19:32 sh.distrib -> bash
-rwxr-xr-x 1 root root   26060 2009-04-13 19:32 sleep
-rwxr-xr-x 1 root root   48708 2009-04-13 19:32 stty
-rwsr-xr-x 1 root root   31012 2009-04-13 19:32 su
-rwxr-xr-x 1 root root   26044 2009-04-13 19:32 sync
-rwxr-xr-x 1 root root    9624 2009-04-13 19:32 tailf
-rwxr-xr-x 1 root root  252468 2009-04-13 19:32 tar
lrwxrwxrwx 1 root root      13 2009-04-13 19:32 tcsh -> /usr/bin/tcsh
-rwxr-xr-x 1 root root    9516 2009-04-13 19:32 tempfile
-rwxr-xr-x 1 root root   46616 2009-04-13 19:32 touch
-rwxr-xr-x 1 root root   26036 2009-04-13 19:32 true
-rwxr-xr-x 1 root root    9664 2009-04-13 19:32 ulockmgr_server
-rwsr-xr-x 1 root root   71556 2009-04-13 19:32 umount
-rwxr-xr-x 1 root root   26052 2009-04-13 19:32 uname
-rwxr-xr-x 1 root root      63 2009-04-13 19:32 uncompress
-rwxr-xr-x 1 root root    3089 2009-04-13 19:32 unicode_start
-rwxr-xr-x 1 root root   96220 2009-04-13 19:32 vdir
-rwxr-xr-x 1 root root     946 2009-04-13 19:32 which
-rwxr-xr-x 1 root root      64 2009-04-13 19:32 zcat
-rwxr-xr-x 1 root root      69 2009-04-13 19:32 zcmp
-rwxr-xr-x 1 root root    4424 2009-04-13 19:32 zdiff
-rwxr-xr-x 1 root root      64 2009-04-13 19:32 zegrep
-rwxr-xr-x 1 root root      64 2009-04-13 19:32 zfgrep
-rwxr-xr-x 1 root root    2015 2009-04-13 19:32 zforce
-rwxr-xr-x 1 root root    4898 2009-04-13 19:32 zgrep
-rwxr-xr-x 1 root root    1733 2009-04-13 19:32 zless
-rwxr-xr-x 1 root root    2416 2009-04-13 19:32 zmore
-rwxr-xr-x 1 root root    4952 2009-04-13 19:32 znew
ubuntu@ubuntu:~$ 

```

Thanks for your quick replies, your help is really appreciated.

---

### Post by meierfra. on 2009-04-14
I don't know  what the problem could be. So lets try a different approach:

Open the file "menu.lst":

```
gksudo gedit /mnt/boot/grub/menu.lst
```

Add this to the very end of the file:

title Ubuntu
root (hd0,2)
kernel /vmlinuz root=/dev/sda3 ro
initrd /initrd.img

Save the file. Reboot with the bios set to boot from the Ubuntu drive.

---

### Post by RonPDX on 2009-04-14
For some reason ```
gksudo gedit /mnt/boot/grub/menu.lst
``` will not open when using a terminal. I tried saving the file after opening mousepad but I cannot save the file (permissions issue).

I am thinking about just starting out fresh with a fresh install if we can not get this working. If I remember correctly I should be able to over the Ubuntu partition with a live CD then set-up dual boot during the installation process?

---

### Post by meierfra. on 2009-04-14
Are you using Xubuntu?
Did you use "gksudo mousepad /mnt/boot/grub/menu.lst"?

You might also try

```
sudo nano /mnt/boot/grub/menu.lst
```

(also I fixed a typo in my previous post, "intird->initrd"



> I am thinking about just starting out fresh with a fresh install if we can not get this working.

That might not be a bad idea. Try my above suggestions, but if none of that works,  a  fresh install is probably your best option.

---

### Post by RonPDX on 2009-04-14
I am actually using Mythbuntu with Ubuntu frontend. 

A quick question before I make the latest change...I noticed this entry:

```
title Mythbuntu
root (hd0,1)
makeactive
chainloader +1
boot

```

...is it ok to place your suggestion after it before I reboot?

---

### Post by meierfra. on 2009-04-14
> ...is it ok to place your suggestion after it before I reboot? 

?? Not sure what you are trying to ask.   But you can place the Ubuntu item I suggested  anywhere you want to.

---

### Post by RonPDX on 2009-04-14
After rebooting unfortunately I got a kernal panic (6.204283)

```
Targer sbin/init

run-init / bin/sh no such file or directory
```

---

### Post by meierfra. on 2009-04-14
> run-init / bin/sh no such file or directory

I'm not surprised. That's basically the same as the "/bin/bash" error earlier.

Maybe it's possible to get around the "/bin/sh" problem. But who knows that else did go wrong in the transfer.

So I suggest to backup up any  valuable data you have on the Ubuntu partition  and then  do a fresh install.

---

### Post by RonPDX on 2009-04-14
I was thinking the same thing, if I had the rely on windoze I might just have to bury my head in a mud pond and hang upside down. 

Thanks again for all of your help, it is people like you that the forums a great place to come and learn.

Ron

---

### Post by meierfra. on 2009-04-14
Are you still able to boot into Windows?

If not, run "fixmbr" from  the recovery console of your Windows CD, or

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

in a  terminal in the LiveCD.


> Thanks again for all of your help, 
Your are welcome.

---

### Post by RonPDX on 2009-04-14
I am actually still able to boot into windows. 

Since this will be my first time installing onto a dedicated partition and not Wubi, is there anything special I should know?

---

### Post by meierfra. on 2009-04-14
Since your partitions are already set up correctly, its probably best to choose "manual"  during the installation instead of guided.  (Otherwise you probably end up with two swap partitions, or things like  that). There aren't any tutorials on manual partition which I really like, but  this  link should give you the basic idea 

[http://mywebsite.bigpond.net.au/dfelderh/p23.html](http://mywebsite.bigpond.net.au/dfelderh/p23.html)

---

### Post by RonPDX on 2009-04-14
Thanks again

---


---
title: "iPod problems..?"
date: 2009-04-05
forum: General Help
---

### Post by blaker1994 on 2009-04-05
Hey everyone, this morning, I was really bored, and currently i have no HDD and am just running off of the LiveCD(which is super small). So, I decided to install ubuntu to my iPod(I knew that it would erase everything). when i set my BIOS it boot from USB i resetted. I got the message "NON SYSTEM DISK ERROR." I popped in my LiveCD, and booted up, and i plugged in my iPod and it's not showing up. It shows up as an "USB Disk" under "Places" and wont let me rescan it. I've tried 
```
sudo fdisk /dev/sda
```
but I get this? 
```
ubuntu@ubuntu:~$ sudo fdisk /dev/sda
Note: sector size is 4096 (not 512)

Command (m for help): l

 0  Empty           1e  Hidden W95 FAT1 80  Old Minix       bf  Solaris        
 1  FAT12           24  NEC DOS         81  Minix / old Lin c1  DRDOS/sec (FAT-
 2  XENIX root      39  Plan 9          82  Linux swap / So c4  DRDOS/sec (FAT-
 3  XENIX usr       3c  PartitionMagic  83  Linux           c6  DRDOS/sec (FAT-
 4  FAT16 <32M      40  Venix 80286     84  OS/2 hidden C:  c7  Syrinx         
 5  Extended        41  PPC PReP Boot   85  Linux extended  da  Non-FS data    
 6  FAT16           42  SFS             86  NTFS volume set db  CP/M / CTOS / .
 7  HPFS/NTFS       4d  QNX4.x          87  NTFS volume set de  Dell Utility   
 8  AIX             4e  QNX4.x 2nd part 88  Linux plaintext df  BootIt         
 9  AIX bootable    4f  QNX4.x 3rd part 8e  Linux LVM       e1  DOS access     
 a  OS/2 Boot Manag 50  OnTrack DM      93  Amoeba          e3  DOS R/O        
 b  W95 FAT32       51  OnTrack DM6 Aux 94  Amoeba BBT      e4  SpeedStor      
 c  W95 FAT32 (LBA) 52  CP/M            9f  BSD/OS          eb  BeOS fs        
 e  W95 FAT16 (LBA) 53  OnTrack DM6 Aux a0  IBM Thinkpad hi ee  GPT            
 f  W95 Ext'd (LBA) 54  OnTrackDM6      a5  FreeBSD         ef  EFI (FAT-12/16/
10  OPUS            55  EZ-Drive        a6  OpenBSD         f0  Linux/PA-RISC b
11  Hidden FAT12    56  Golden Bow      a7  NeXTSTEP        f1  SpeedStor      
12  Compaq diagnost 5c  Priam Edisk     a8  Darwin UFS      f4  SpeedStor      
14  Hidden FAT16 <3 61  SpeedStor       a9  NetBSD          f2  DOS secondary  
16  Hidden FAT16    63  GNU HURD or Sys ab  Darwin boot     fb  VMware VMFS    
17  Hidden HPFS/NTF 64  Novell Netware  b7  BSDI fs         fc  VMware VMKCORE 
18  AST SmartSleep  65  Novell Netware  b8  BSDI swap       fd  Linux raid auto
1b  Hidden W95 FAT3 70  DiskSecure Mult bb  Boot Wizard hid fe  LANstep        
1c  Hidden W95 FAT3 75  PC/IX           be  Solaris boot    ff  BBT            

``` 
```
ubuntu@ubuntu:~$ sudo mount /media/sda
mount: can't find /media/sda in /etc/fstab or /etc/mtab

```
Mind youd, that I am using the LiveCD, so i am under "Ubuntu"
What do i do from here?

---

### Post by yamarc on 2009-04-05
Run and post the result of:

```
ls -l /dev | grep ^b
```

---

### Post by blaker1994 on 2009-04-05
```
ubuntu@ubuntu:~$ ls -l /dev | grep ^b
brw-rw----  1 root   disk      7,   0 2008-10-29 22:54 loop0
brw-rw----  1 root   disk      7,   1 2009-04-05 11:35 loop1
brw-rw----  1 root   disk      7,   2 2009-04-05 11:35 loop2
brw-rw----  1 root   disk      7,   3 2009-04-05 11:35 loop3
brw-rw----  1 root   disk      7,   4 2009-04-05 11:35 loop4
brw-rw----  1 root   disk      7,   5 2009-04-05 11:35 loop5
brw-rw----  1 root   disk      7,   6 2009-04-05 11:35 loop6
brw-rw----  1 root   disk      7,   7 2009-04-05 11:35 loop7
brw-rw----  1 root   disk      1,   0 2009-04-05 11:34 ram0
brw-rw----  1 root   disk      1,   1 2009-04-05 11:34 ram1
brw-rw----  1 root   disk      1,  10 2009-04-05 11:34 ram10
brw-rw----  1 root   disk      1,  11 2009-04-05 11:34 ram11
brw-rw----  1 root   disk      1,  12 2009-04-05 11:34 ram12
brw-rw----  1 root   disk      1,  13 2009-04-05 11:34 ram13
brw-rw----  1 root   disk      1,  14 2009-04-05 11:34 ram14
brw-rw----  1 root   disk      1,  15 2009-04-05 11:34 ram15
brw-rw----  1 root   disk      1,   2 2009-04-05 11:34 ram2
brw-rw----  1 root   disk      1,   3 2009-04-05 11:34 ram3
brw-rw----  1 root   disk      1,   4 2009-04-05 11:34 ram4
brw-rw----  1 root   disk      1,   5 2009-04-05 11:34 ram5
brw-rw----  1 root   disk      1,   6 2009-04-05 11:34 ram6
brw-rw----  1 root   disk      1,   7 2009-04-05 11:34 ram7
brw-rw----  1 root   disk      1,   8 2009-04-05 11:34 ram8
brw-rw----  1 root   disk      1,   9 2009-04-05 11:34 ram9
brw-rw----  1 root   disk    254,   0 2009-04-05 11:34 ramzswap0
brw-rw----+ 1 root   cdrom    11,   0 2009-04-05 11:34 scd0
brw-rw----+ 1 root   disk      8,   0 2009-04-05 11:36 sda
```

---

### Post by corpsehacker on 2009-04-05
I thought that Ipods use a one way data transfer system where data can go in but never come out. ( This is to protect from people putting music on an Ipod and then putting it on another computer)

---

### Post by yamarc on 2009-04-05
I never tried playing with iPods (don't even own one) but you can try running 'cfdisk', creating a primary partition on the iPod and setting its 'Bootable' flag to true, and then run:

```
mkfs.ext3 /dev/sda
```

and then run the Ubuntu installer to install on sda.

---

### Post by blaker1994 on 2009-04-05
I have no clue, I'm a novice at this, but why does my ipod have partitions? I think that is what that last thing i did is.. :mad:

---

### Post by blaker1994 on 2009-04-05
when i make a new partiton, will it still restore if i hk it up to an itunes?

---

### Post by blaker1994 on 2009-04-05
```
   Wrote partition table, but re-read table failed.  Reboot to update table.
                 Toggle bootable flag of the current partition

```
\did it work?

---

### Post by yamarc on 2009-04-05
Nope. Before you run cfdisk, make sure to unmount your iPod. (You can do this easily by right-clicking its desktop icon and clicking 'Eject')

---

### Post by blaker1994 on 2009-04-05
no icon appears on the desktop..?

---

### Post by blaker1994 on 2009-04-05
oh and my ipod says 0KBs.. even though nothing is on it.. ?

---

### Post by yamarc on 2009-04-05
Can you print the results of 'mount'?

---

### Post by blaker1994 on 2009-04-05
Print to where?

```
 Enter filename or press RETURN to display on screen:
```

---

### Post by yamarc on 2009-04-05
Oops, didn't explain myself properly.
I meant to say, can you post the results of the command 'mount' here?

---

### Post by blaker1994 on 2009-04-05
ubuntu@ubuntu:~$ mount
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

---


---
title: "General Booting mess-up"
date: 2008-12-27
forum: General Help
---

### Post by pappasadrian on 2008-12-27
I am a new user of Ubuntu. well, here is my story:
I have a Toshiba laptop P-25 with 80GB internal HD, on which Windows XP are installed. This HD is not partitioned, and most of it (about 76GB) is full of programs, windows data, and various files.
I decided to install ubuntu on my external WD HD (250GB), which already had some files (other than the files on the internal HD) on it (50GB). I made a second partition on which I would install Ubuntu 8.10, using the Live CD. So now I have one FAT32 partition with my files, and one ext2 partition with Ubuntu. No problem in that part.
Ubuntu was running fine, even though I couldn't access the internal HD, which is NTFS. The other 2 partitions on the external HD could be accessed normally.
I did some updates I was prompted to do (~200MB), and I restarted the PC, in order for the updates to take place. However, I didn't boot in Ubuntu, but in XP, since I needed to access some programs there. But none of the 2 partitions were recognised. Disk management said that both the partitions were "Healthy (unknown partition)"
Trying to go back to Ubuntu to figure out what is going on, when I rebooted the PC, I get an Error 22 in GRUB. So I cannot boot either XP or Ubuntu. 
The only way to open the PC is via Ubuntu Live CD, but this way I cannot access any partition or HD.

My priorities at this point are:
1) Rescue the files on the FAT32 partition on the external HD
2) Rescue the files on the internal NTFS HD
3) Rescue Windows XP
4) Get Ubuntu to work

I don't know why GRUB is installed on my system. I believe that the best way to get access at least to XP is to override it somehow.

Any help whatsoever whould be appreciated

---

### Post by pappasadrian on 2008-12-27
PS: I haven't got Windows CD (lost them...)

---

### Post by caljohnsmith on 2008-12-27
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what your problem might be.

---

### Post by pappasadrian on 2008-12-28
> ============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for its boot files.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Mounting failed:  
Windows is hibernated, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is hibernated. Please resume and shutdown Windows
properly, or mount the volume read-only with the 'ro' mount option, or
mount the volume read-write with the 'remove_hiberfile' mount option.
For example type on the command line:

            mount -t ntfs-3g /dev/sda1 sda1 -o remove_hiberfile


sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Mounting failed:  
mount: /dev/sdb1: can't read superblock

sdb2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  No Boot Loader
    Mounting failed:  
mount: Stale NFS file handle

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xba92ba92

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   156296384    78148161    7  HPFS/NTFS

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    98960399    49480168+   c  W95 FAT32 (LBA)
/dev/sdb2        98960400   308673791   104856696   83  Linux

sfdisk -V /dev/sdb:

/dev/sdb: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="40F8F50BF8F4FFC8" LABEL="S3A1519D001" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: LABEL="SMALL HD" UUID="7C98-D5AB" TYPE="vfat" 
/dev/sdb2: UUID="7879062a-c5c3-4990-9b2e-868e5693fa74" TYPE="ext2" 

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

=============================== StdErr Messages: ===============================

Unknown BootLoader  on /dev/sdb1

00000000  eb 5a 90 4d 53 57 49 4e  34 2e 31 00 02 40 38 00  |.Z.MSWIN4.1..@8.|
00000010  02 00 00 00 00 f8 00 00  3f 00 10 00 3f 00 00 00  |........?...?...|
00000020  d1 03 e6 05 2f 2f 00 00  00 00 00 00 cf 05 00 00  |....//..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 ab d5 98 7c 4e  4f 20 4e 41 4d 45 20 20  |..)...|NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 f1 7d fa 33 c9 8e  |  FAT32   .}.3..|
00000060  d1 bc f8 7b 8e c1 bd 78  00 c5 76 00 1e 56 16 55  |...{...x..v..V.U|
00000070  bf 22 05 89 7e 00 89 4e  02 b1 0b fc f3 a4 8e d9  |."..~..N........|
00000080  bd 00 7c c6 45 fe 0f 8b  46 18 88 45 f9 fb 38 66  |..|.E...F..E..8f|
00000090  40 7c 04 cd 13 72 4e bf  02 00 83 7e 16 00 75 71  |@|...rN....~..uq|
000000a0  66 83 7e 24 00 74 6a 8b  46 1c 8b 56 1e b9 03 00  |f.~$.tj.F..V....|
000000b0  49 40 75 01 42 bb 00 7e  e8 90 00 73 2a b0 f8 4f  |I@u.B..~...s*..O|
000000c0  74 21 8b 46 32 33 d2 b9  03 00 3b c8 77 43 8b 76  |t!.F23....;.wC.v|
000000d0  0e 3b ce 73 3c 2b f1 3b  c6 77 36 03 46 1c 13 56  |.;.s<+.;.w6.F..V|
000000e0  1e eb cd 73 2c eb 49 66  81 be 00 02 52 52 61 41  |...s,.If....RRaA|
000000f0  75 cc 66 81 be fc 03 00  00 55 aa 75 c1 66 81 be  |u.f......U.u.f..|
00000100  fc 05 00 00 55 aa 75 b6  83 7e 2a 00 77 03 e9 ef  |....U.u..~*.w...|
00000110  02 be 80 7d fb ac 98 03  f0 ac 84 c0 74 17 3c ff  |...}........t.<.|
00000120  74 09 b4 0e bb 07 00 cd  10 eb ee be 83 7d eb e4  |t............}..|
00000130  be 81 7d eb df 33 c0 cd  16 5e 1f 8f 04 8f 44 02  |..}..3...^....D.|
00000140  cd 19 00 00 00 00 00 00  00 00 00 50 52 51 91 92  |...........PRQ..|
00000150  33 d2 f7 76 18 91 f7 76  18 42 87 ca f7 76 1a 8a  |3..v...v.B...v..|
00000160  f2 8a 56 40 8a e8 d0 cc  d0 cc 0a cc b8 01 02 cd  |..V@............|
00000170  13 59 5a 58 72 09 40 75  01 42 03 5e 0b e2 cc c3  |.YZXr.@u.B.^....|
00000180  03 18 01 27 0d 0a 49 6e  76 61 6c 69 64 20 73 79  |...'..Invalid sy|
00000190  73 74 65 6d 20 64 69 73  6b ff 0d 0a 44 69 73 6b  |stem disk...Disk|
000001a0  20 49 2f 4f 20 65 72 72  6f 72 ff 0d 0a 52 65 70  | I/O error...Rep|
000001b0  6c 61 63 65 20 74 68 65  20 64 69 73 6b 2c 20 61  |lace the disk, a|
000001c0  6e 64 20 74 68 65 6e 20  70 72 65 73 73 20 61 6e  |nd then press an|
000001d0  79 20 6b 65 79 0d 0a 00  49 4f 20 20 20 20 20 20  |y key...IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 80 01  |SYSMSDOS   SYS..|
000001f0  00 57 49 4e 42 4f 4f 54  20 53 59 53 00 00 55 aa  |.WINBOOT SYS..U.|
00000200

No errors were reported.


This is it...

---

### Post by caljohnsmith on 2008-12-28
So let me see if I understand correctly: you were able to access your FAT partition and even boot into Windows before, but when you installed some updates in Ubuntu recently, that's when everything broke? 

From your Live CD, how about first trying:
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
```
Please post the output of the above commands, and if the ntfsfix completes successfully, then try:
```
sudo mkdir /media/sda1 && sudo mount /dev/sda1 /media/sda1
nautilus /media/sda1 &
```
And if you can make it that far, you should be able to see your Windows files in the file browser that pops up. Next try:
```
sudo fsck -yCM /dev/sdb2
```
And please post the output. And lastly, how about booting your Windows Install CD, go to the "recovery console", and do:
```
map
```
Find the drive letter of both your Windows partition and the FAT partition, and then do:
```
chkdsk /r C:
```
And run the chkdsk command on both your Windows partition and FAT partition by substituting the appropriate drive letter in the above command. Also run chkdsk on each partition as many times as it takes until it reports no errors. Then reboot into Ubuntu and see if you can mount their partitions again. Let me know how it goes.

---

### Post by pappasadrian on 2008-12-28
> **caljohnsmith said:**
> From your Live CD, how about first trying:
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
```


```
ubuntu@ubuntu:~$ sudo apt-get install ntfsprogs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfsprogs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu:~$ sudo ntfsfix /dev/sda1
Mounting volume... FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
Remount failed: Operation not permitted.
```

But i finally managed to delete the hiberfile, so I got access to sda1
```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /media/sda1
Windows is hibernated, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is hibernated. Please resume and shutdown Windows
properly, or mount the volume read-only with the 'ro' mount option, or
mount the volume read-write with the 'remove_hiberfile' mount option.
For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/sda1 -o remove_hiberfile

ubuntu@ubuntu:~$  mount -t ntfs-3g /dev/sda1 /media/sda1 -o remove_hiberfile
mount: only root can do that
ubuntu@ubuntu:~$ sudo  mount -t ntfs-3g /dev/sda1 /media/sda1 -o remove_hiberfile

```

> **caljohnsmith said:**
> Next try:
Code:

sudo fsck -yCM /dev/sdb2

And please post the output.

```
ubuntu@ubuntu:~$ sudo fsck -yCM /dev/sdb2
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext2: No such file or directory while trying to open /dev/sdb2

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```
 
I tried the suggested alternative superblock, but got exactly the same message...




Ill let you know the results with windows CD asap (once I gain access to a CD)
Please, suggest a way to access sdb1, or a program that might help me obtain my files

---

### Post by caljohnsmith on 2008-12-28
If that last mount command your ran that removes the hibernate file worked, you should have Windows mounted on /media/sda1. So after you mount it with the command you used, you could do:
```
nautilus /media/sda1 &
```
And that should allow you to access your Windows partition. But about the superblock problem with sdb2, you could try following [this post]("http://ubuntuforums.org/showpost.php?p=5806996") and see if it helps. Let me know how it goes.

---

### Post by pappasadrian on 2008-12-28
> **caljohnsmith said:**
> If that last mount command your ran that removes the hibernate file worked, you should have Windows mounted on /media/sda1. So after you mount it with the command you used, you could do:
```
nautilus /media/sda1 &
```
And that should allow you to access your Windows partition. But about the superblock problem with sdb2, you could try following [this post]("http://ubuntuforums.org/showpost.php?p=5806996") and see if it helps. Let me know how it goes.

Thanks for the quick reply.
I have access of the windows HD (sda1), I can browse files. Thanks

I am working on the other method you just suggested, will let you know ASAP

---

### Post by pappasadrian on 2008-12-28
```
ubuntu@ubuntu:~$ sudo dumpe2fs /dev/sdb1 | grep -i "block size"
dumpe2fs 1.41.3 (12-Oct-2008)
dumpe2fs: Bad magic number in super-block while trying to open /dev/sdb1
```

This is what I got...

---

### Post by caljohnsmith on 2008-12-28
You have to modify those commands in the tutorial to use sdb2, which is your Ubuntu partiton, so you would need to do:
```
sudo dumpe2fs /dev/[COLOR="Blue"]sdb2[/COLOR] | grep -i "block size"
```
Try that and see if it works, and if not, let me know what errors you get.

---

### Post by pappasadrian on 2008-12-28
...

---

### Post by pappasadrian on 2008-12-28
I did change that... 
```
ubuntu@ubuntu:~$  sudo dumpe2fs /dev/sdb2 | grep -i "block size"
dumpe2fs 1.41.3 (12-Oct-2008)
Block size:               4096
ubuntu@ubuntu:~$ sudo dumpe2fs /dev/sdb2 | grep superblock
dumpe2fs 1.41.3 (12-Oct-2008)
  Primary superblock at 0, Group descriptors at 1-7
  Backup superblock at 32768, Group descriptors at 32769-32775
  Backup superblock at 98304, Group descriptors at 98305-98311
  Backup superblock at 163840, Group descriptors at 163841-163847
  Backup superblock at 229376, Group descriptors at 229377-229383
  Backup superblock at 294912, Group descriptors at 294913-294919
  Backup superblock at 819200, Group descriptors at 819201-819207
  Backup superblock at 884736, Group descriptors at 884737-884743
  Backup superblock at 1605632, Group descriptors at 1605633-1605639
  Backup superblock at 2654208, Group descriptors at 2654209-2654215
  Backup superblock at 4096000, Group descriptors at 4096001-4096007
  Backup superblock at 7962624, Group descriptors at 7962625-7962631
  Backup superblock at 11239424, Group descriptors at 11239425-11239431
  Backup superblock at 20480000, Group descriptors at 20480001-20480007
  Backup superblock at 23887872, Group descriptors at 23887873-23887879

ubuntu@ubuntu:~$ sudo mount -o sb=$[4*32768] /dev/sdb2 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

I got the same error for every superblock listed...
However, I dont care about sdb2 so much, only ubuntu os is on it. I can always find that again...
I am worried about sdb1, where all my important files are.
"mount: /dev/sdb1: can't read superblock" 

Thanks though for your help and interest so far. I really appreciate that.

---

### Post by caljohnsmith on 2008-12-28
Since you mentioned sdb2 is not a big concern, I would go ahead and reinstall Ubuntu then. Good luck and let me know how it goes.

---


---
title: "Grub Error 17 + partition no longer exists!"
date: 2009-03-02
forum: General Help
---

### Post by linuxisevolution on 2009-03-02
I cannot even get to the grub menu. I am using a livecd now. Somehow the partitions deleted themselves. fdisk -l 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x54b654b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15057   120945321    7  HPFS/NTFS
/dev/sda2           15058       29772   118198237+  83  Linux
/dev/sda3           29773       30087     2530237+   5  Extended
/dev/sda4           30088       30401     2522205   82  Linux swap / Solaris
/dev/sda5           29773       30087     2530206   82  Linux swap / Solaris

I am trying to reinstall grub, but when I type:

find /boot/grub/stage1

I get:

Error 15: File not found

Please, someone help. :(

---

### Post by caljohnsmith on 2009-03-02
In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by linuxisevolution on 2009-03-02
Here is the file. *Note that sda2 is my Ubuntu partition.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x54b654b6

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   241,890,704   241,890,642   7 HPFS/NTFS
/dev/sda2         241,890,705   478,287,179   236,396,475  83 Linux
/dev/sda3         478,287,180   483,347,654     5,060,475   5 Extended
/dev/sda5         478,287,243   483,347,654     5,060,412  82 Linux swap / Solaris
/dev/sda4         483,347,655   488,392,064     5,044,410  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00042ea4

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="3CE8AB85E8AB3C50" TYPE="ntfs" 
/dev/sda4: LABEL="swap2" UUID="c6a52d5c-6be7-48ec-ac13-763f6b915669" TYPE="swap" 
/dev/sda5: UUID="7a63a999-b4ed-4a59-bae4-3b369feb4611" TYPE="swap" 
/dev/sdb1: UUID="89272af4-0fd4-4a91-b423-89243712c302" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

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
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

---

### Post by caljohnsmith on 2009-03-02
The script was not able to mount your sda2 partition, nor was "blkid" able to detect what type of file system it is. What did you do just prior to getting the Grub error and having problems with Ubuntu? How about posting the output of:
```
sudo e2fsck -fv /dev/sda2
```

---

### Post by linuxisevolution on 2009-03-02
> **caljohnsmith said:**
> The script was not able to mount your sda2 partition, nor was "blkid" able to detect what type of file system it is. What did you do just prior to getting the Grub error and having problems with Ubuntu? How about posting the output of:
```
sudo e2fsck -fv /dev/sda2
```

I am not sure about what happened. My mother was using the machine and said it was acting funny and then when she restarted it said grub error 17. I also know she was using Limewire. I will get back on that machine now to run that command...

---

### Post by linuxisevolution on 2009-03-02
This is the output of that command:

e2fsck 1.41.3 (12-Oct-2008)
e2fsck: Superblock invalid, trying backup blocks...
ext3 recovery flag is clear, but journal has data.
Recovery flag not set in backup superblock, so running journal anyway.
/dev/sda2: recovering journal
Pass 1: Checking inodes, blocks, and sizes
Deleted inode 802985 has zero dtime.  Fix<y>? yes

---

### Post by linuxisevolution on 2009-03-02
Here is the rest:
Fix<y>? yes

Free inodes count wrong for group #812 (8192, counted=5870).
Fix<y>? yes


Free inodes count wrong for group #814 (8192, counted=4789).
Fix<y>? yes

Directories count wrong for group #814 (0, counted=476).
Fix<y>? yes

Free inodes count wrong for group #815 (8192, counted=6762).
Fix<y>? yes

Directories count wrong for group #815 (0, counted=534).
Fix<y>? yes

Free inodes count wrong for group #816 (8192, counted=6013).
Fix<y>? yes

Directories count wrong for group #816 (0, counted=534).
Fix<y>? yes

Free inodes count wrong for group #817 (8192, counted=6631).
Fix<y>? yes

Directories count wrong for group #817 (0, counted=534).
Fix<y>? yes

Free inodes count wrong for group #818 (8192, counted=5938).
Fix<y>? yes

Directories count wrong for group #818 (0, counted=109).
Fix<y>? yes

Free inodes count wrong for group #819 (8192, counted=4537).
Fix<y>? yes

Directories count wrong for group #819 (0, counted=143).
Fix<y>? yes

Free inodes count wrong for group #820 (8192, counted=5995).
Fix<y>? yes

Directories count wrong for group #820 (0, counted=534).
Fix<y>? yes

Free inodes count wrong for group #821 (8192, counted=6941).
Fix<y>? yes

Directories count wrong for group #821 (0, counted=534).
Fix<y>? yes

Free inodes count wrong for group #822 (8192, counted=5649).
Fix<y>? yes

Directories count wrong for group #822 (0, counted=271).
Fix<y>? yes

Free inodes count wrong for group #823 (8192, counted=5829).
Fix<y>? yes

Directories count wrong for group #823 (0, counted=407).
Fix<y>? yes

Free inodes count wrong for group #824 (8192, counted=5941).
Fix<y>? yes

Directories count wrong for group #824 (0, counted=297).
Fix<y>? yes

Free inodes count wrong for group #825 (8192, counted=5937).
Fix<y>? yes

Directories count wrong for group #825 (0, counted=43).
Fix<y>? yes

Free inodes count wrong for group #826 (8192, counted=5647).
Fix<y>? yes

Directories count wrong for group #826 (0, counted=140).
Fix<y>? yes

Free inodes count wrong for group #827 (8192, counted=6250).
Fix<y>? yes

Directories count wrong for group #827 (0, counted=333).
Fix<y>? yes

Free inodes count wrong for group #828 (8192, counted=7558).
Fix<y>? yes

Directories count wrong for group #828 (0, counted=59).
Fix<y>? yes

Free inodes count wrong for group #838 (8192, counted=8187).
Fix<y>? yes

Free inodes count wrong for group #842 (8192, counted=8162).
Fix<y>? yes

Free inodes count wrong for group #849 (8192, counted=8187).
Fix<y>? yes

Free inodes count wrong for group #853 (8192, counted=8116).
Fix<y>? yes

Free inodes count wrong for group #856 (8192, counted=8037).
Fix<y>? yes

Free inodes count wrong for group #858 (8192, counted=8190).
Fix<y>? yes

Free inodes count wrong for group #880 (8192, counted=8191).
Fix<y>? yes

Free inodes count wrong for group #884 (8192, counted=8191).
Fix<y>? yes

Free inodes count wrong for group #898 (8192, counted=8190).
Fix<y>? yes

Free inodes count wrong (7389173, counted=7205261).
Fix<y>? yes


/dev/sda2: ***** FILE SYSTEM WAS MODIFIED *****

  183923 inodes used (2.49%)
    3983 non-contiguous inodes (2.2%)
         # of inodes with ind/dind/tind blocks: 10857/424/0
 5068356 blocks used (17.15%)
       0 bad blocks
       2 large files

  143689 regular files
   20411 directories
     135 character device files
      43 block device files
      20 fifos
     510 links
   19585 symbolic links (18125 fast symbolic links)
      31 sockets
--------
  184424 files

---

### Post by linuxisevolution on 2009-03-02
Thank you so much!!!!! That command fixed the partition, I was then able to reinstall grub :KS

---

### Post by caljohnsmith on 2009-03-02
That's great news, I'm so glad to hear you can boot Ubuntu again. You might want to ask your mother what she was doing that might have corrupted your linux partition just so you can prevent any future accidents. And it goes without saying that it would be a good idea to make sure you have everything important in your Ubuntu install backed up. Anyway, cheers and enjoy Ubuntu and Windows. :)

---


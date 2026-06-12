---
title: "Cannot find grub directory"
date: 2009-05-03
forum: General Help
---

### Post by jerg on 2009-05-03
Hey,
I just re-installed Windows Vista Home Premium, and it wiped out my Grub Bootloader and I can't get back into Ubuntu Linux. I tried the online advice to use a live CD and re-install Grub. But Ubuntu is telling me that the directory "/boot/grub" doesn't exist, so I can't even follow the online advice. The only thing I could recall that I've done wrong is not using the original disc I used to install Ubuntu. I installed Ubuntu 8.04 and I'm trying to fix the issue with the Ubuntu 8.10 disc. What I'm asking is if anyone ever encountered this problem before, or do anyone know how to fix this issue. Anywayz I'll try to fix the issue still but I would apperciate the help if any.

Thanks in advance..........

---

### Post by caljohnsmith on 2009-05-03
I think it would help to first get a clearer picture of your setup, so how about downloading the **Boot Info Script** to your Ubuntu desktop (can be the Live CD):

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

John

---

### Post by jerg on 2009-05-04
Here's the RESULT.TXT file
```

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 63. But according to the info from fdisk, 
                       sdb1 starts at sector 1526175.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x60000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       176,714       176,652  de Dell Utility
/dev/sda2    *        178,176   307,386,367   307,208,192   7 HPFS/NTFS
/dev/sda3         307,387,710   625,137,344   317,749,635   5 Extended
/dev/sda5         612,156,888   625,137,344    12,980,457  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4025 MB, 4025810432 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7862911 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe0909817

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *      1,526,175     3,084,479     1,558,305   6 FAT16
/dev/sdb2                  63     1,526,174     1,526,112  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-0604" TYPE="vfat" 
/dev/sda2: UUID="B272227972224309" TYPE="ntfs" 
/dev/sda5: UUID="5340f411-6885-4f1c-a9d0-5014b9e1f2cb" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
/dev/mmcblk0p1: UUID="49C6-96B9" TYPE="vfat" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="ubuntu810" UUID="49FC-BB87" TYPE="vfat" 
/dev/sdb2: LABEL="casper-rw" UUID="3ee98985-cae2-4080-aa15-e89d165eab51" TYPE="ext2" 

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
/dev/mmcblk0p1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sdb1 on /media/ubuntu810 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sdb2 on /media/casper-rw type ext2 (rw,nosuid,nodev,uhelper=hal)

```

Thanks for the tip I'll see if I can solve the problem myself but still can I have your advice...

Oh yea forgot to mention .....device sdb is my 4GB flash drive I had it in the USB port when I ran the scripted

P.S. Just wanted to know ...how can I save file when I'm running the OS from a Live CD?

---

### Post by caljohnsmith on 2009-05-04
> **jerg said:**
> 
```


Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x60000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       176,714       176,652  de Dell Utility
/dev/sda2    *        178,176   307,386,367   [COLOR="Red"]307,208,192[/COLOR]   7 HPFS/NTFS
/dev/sda3         307,387,710   625,137,344   317,749,635   5 Extended
/dev/sda5         [COLOR="Red"]612,156,888[/COLOR]   625,137,344    12,980,457  82 Linux swap / Solaris

```

It looks like the reason why Ubuntu tells you that the /boot/grub directory doesn't exist is because somehow your Ubuntu partition got deleted. The partition listing for your sda drive above does not show any linux partitions, and there is a large ~145 GiB block of unused space after the end of the sda2 partition before the sda5 partition begins. I would suggest using testdisk to recover your Ubuntu partition, so if that sounds good to you, how about downloading the [testdisk-6.11.1.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.11.1.linux26.tar.bz2") package to your Ubuntu Live CD desktop, and then do:
```

cd ~/Desktop
tar xvf testdisk-6.11.1.linux26.tar.bz2
sudo testdisk-6.11/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", "Proceed", "Intel", "Analyze", "Quick search", "Y" to search for Vista partitions, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and also which of those partitions seem to be your existing partitions. We can work from there.

John

---

### Post by jerg on 2009-05-04
This is what I got when I ran the program

```
ubuntu@ubuntu:~/Desktop$ sudo testdisk-6.11.1/linux/testdisk_static
Segmentation fault (core dumped)

```

don't know what that means.....

---

### Post by caljohnsmith on 2009-05-05
I'm surprised testdisk 6.11 crashed for you--just to confirm, are you using an 8.10 Live CD? How about trying again, but this time with testdisk 6.10; you can download the 6.10 package to your desktop from:

[http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2)

And then try running it with:
```

cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static
```
If that works, proceed with the directions from my previous post, and if not, let me know.

John

---

### Post by jerg on 2009-05-05
Hey man thanks for the help so far ....I really want my files back but if I can't get it back I'll have to deal with that...

I don't know if this is correct but I think this is the  output screen you wanted:

```
TestDisk 6.10, Data Recovery Utility, July 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1    10 254 63     176652 [DellUtility]
P FAT32 LBA               11   0  1  4188 254 63   67119570 [NO NAME]
L Linux                19134   1  1 38104 254 63  304769052
L Linux Swap           38105   1  1 38912 254 63   12980457









Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
FAT16, 90 MB / 86 MiB
```

When I highlighted "Linux" Partition the bottom of the screen displayed:

```
EXT3 Large file Sparse superblock, 156 GB / 145 GiB
```

ans when I highlighted "FAT32 LBA" Partition the bottom of the screen displayed:

```
FAT32, 34 GB / 32 GiB
```

And when I viewed the "Linux" or "FAT32 LBA" partition with "p" it returns a message that say:

```
No File or Filesystem Damage
```

Not sure if those are the exact words, but it's something around that line.

Yea then I accidentally Ctrl-C out of the program. (Wanted to copy the text ....$h#7 happens.....lol)

What was strange is that it didn't display any filesystem for the "FAT32 LBA" partition ....which I assume to be the Windows Partition ....it only displayed the same error message as the "Linux" partition

anywayz thanks again, hey if its too much trouble don't worry yourself mein I'll reformat the hard drive, but if you know what's the matter well I would appreciate the extended help but if its a brain-buster .......don't worry

Jerg

---

### Post by caljohnsmith on 2009-05-06
Are you sure what you posted is the output screen after doing the "deep search" in testdisk? It looks like that testdisk screen you posted might only be from the "quick search". It's imperative that you use the "deep search" function, because for one thing, testdisk didn't even find your current Vista partition in the screen you posted. Also, it takes several minutes for the deep search to scan your HDD, and testdisk shows a screen where it counts through your HDD cylinders as it is scanning--did you see that before getting the results screen that you posted? I would suggest trying again, because unfortunately the results you posted are not going to help us recover your partitions. 

John

---

### Post by jerg on 2009-05-23
Hey,
John I got what you wanted, I wasn't seeing an option for a "Quick Search" however when I got the result screen after selecting the "Analyse" option ...it had an option to continue so I did and I got what you wanted here it is:

```
TestDisk 6.10, Data Recovery Utility, July 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1    10 254 63     176652 [DellUtility]
D FAT32 LBA               11   0  1  4188 254 63   67119570 [NO NAME]
D HPFS - NTFS             11  23 13 19133 233 44  307208192
D HPFS - NTFS          11484 122 31 19133 103 42  122880000
D Linux                19134   1  1 38104 254 59  304769048
D Linux                19134   2  1 19320 254 58    3004024
D Linux                19321   1  1 37336 254 62  289426976
D Linux                19325   3  7 37341   2  5  289426976
D Linux                19327  13 15 37343  12 13  289426976
D Linux                19329 185 57 37345 184 55  289426976
D Linux                19330  60 59 37346  59 57  289426976
D Linux                19330 125 60 37346 124 58  289426976
D Linux                19333  43 39 37349  42 37  289426976
Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
FAT16, 90 MB / 86 MiB

```
```

* File Listings *
  =============

1.) FAT16 >32M 
    ===========
-r-xr-xr-x     0     0     29690 25-Jul-2005 16:48 DELLBIO.BIN
-r-xr-xr-x     0     0     33352 21-Jun-2005 16:54 DELLRMK.BIN
-rwxr-xr-x     0     0      1050 31-Mar-2008 18:37 AUTOEXEC.UP
-rwxr-xr-x     0     0       137 31-Mar-2008 18:37 CONFIG.UP
-rwxr-xr-x     0     0        85 31-Mar-2008 18:37 COPYUP.BAT
-rwxr-xr-x     0     0       320 31-Mar-2008 18:37 DELLDIAG.INI
drwxr-xr-x     0     0         0  4-Jun-2008 08:37 DIAGS
-rwxr-xr-x     0     0     15299 31-Mar-2008 18:37 HIMEM.SYS
-rwxr-xr-x     0     0      1050  4-Jun-2008 08:37 AUTOEXEC.BAT
-rwxr-xr-x     0     0       137  4-Jun-2008 08:37 CONFIG.SYS
-rwxr-xr-x     0     0         7 25-Jun-2008 15:51 OOBEDONE.FLG

2.) FAT32 LBA
    =========
-rwxr-xr-x     0     0   251789058  6-Jul-1913 08:31 ^].A^L
-rwxr-xr-x     0     0   4294823093 24-Dec-1970 16:37 .
-rwxr-xr-x     0     0   2215632443 12-Sep-1913 17:31 uVVVVV.
-rwxr-xr-x     0     0    107462 24-Jun-1971 17:31 ^DZ;&#649;.
-r-xr-xr-x     0     0   4294966768  1-Jan-1980 00:59 ^Am.^G
-r-xr-xr-x     0     0   898437119 29-Feb-1948 10:47 ^BR
-rwxr-xr-x     0     0   4294966768  3-Oct-2013 02:11
-rwxr-xr-x     0     0   2215604217  7-Jan-1980 03:44 ^?/
-rwxr-xr-x     0     0   2298478597 25-Oct-1987 07:12 ^T^F
-r-xr-xr-x     0     0   97839615  9-Jan-2033 08:04 .

3.) HPFS - NTFS
    ===========
dr-xr-xr-x     0     0         0  1-May-2009 23:39 .
dr-xr-xr-x     0     0         0  1-May-2009 23:39 ..
dr-xr-xr-x     0     0         0  1-May-2009 23:42 $Recycle.Bin
-r--r--r--     0     0        24  1-May-2009 23:42 autoexec.bat
dr-xr-xr-x     0     0         0  1-May-2009 23:51 Boot
-r--r--r--     0     0    333203  1-May-2009 23:51 bootmgr
-r--r--r--     0     0      8192  1-May-2009 23:51 BOOTSECT.BAK
dr-xr-xr-x     0     0         0 11-May-2009 02:45 Cakewalk Projects
-r--r--r--     0     0        10 18-Sep-2006 21:43 config.sys
dr-xr-xr-x     0     0         0  1-May-2009 22:20 dell
dr-xr-xr-x     0     0         0  1-May-2009 23:42 Documents and Settings
-r--r--r--     0     0   3756064768  1-May-2009 22:59 hiberfil.sys
-r--r--r--     0     0         0  6-May-2009 15:17 IO.SYS
-r--r--r--     0     0         0  6-May-2009 15:17 MSDOS.SYS
-r--r--r--     0     0   4069675008  1-May-2009 22:52 pagefile.sys
dr-xr-xr-x     0     0         0  1-May-2009 23:42 PerfLogs
dr-xr-xr-x     0     0         0  1-May-2009 23:42 Program Files
dr-xr-xr-x     0     0         0  1-May-2009 23:42 ProgramData
dr-xr-xr-x     0     0         0  9-May-2009 23:55 Programming
dr-xr-xr-x     0     0         0  1-May-2009 22:52 System Volume Information
-r--r--r--     0     0   4380160  2-May-2004 22:21 unetbtin.exe
dr-xr-xr-x     0     0         0  1-May-2009 23:42 Users
dr-xr-xr-x     0     0         0  1-May-2009 23:42 Windows


4.) HPFS - NTFS 
    ===========
No file found, filesystem seems damaged.

5.) Linux
    =====
No file found, filesystem seems damaged.

6.) Linux
    =====
drwxr-xr-x     0     0      4096 13-Jul-2008 11:41 .
drwxr-xr-x     0     0      4096 13-Jul-2008 11:41 ..
drwx------     0     0     16384 12-Jul-2008 14:34 lost+found
drwxr-xr-x     0     0      4096 12-Jul-2008 14:34 var
drwxr-xr-x     0     0      4096 12-Jul-2008 14:34 etc
drwxr-xr-x     0     0      4096 12-Jul-2008 14:34 media
lrwxrwxrwx     0     0        11 12-Jul-2008 14:34 cdrom
drwxr-xr-x     0     0      4096 12-Jul-2008 14:34 bin
drwxr-xr-x     0     0      4096 12-Jul-2008 14:34 boot
drwxr-xr-x     0     0      4096 12-Jul-2008 14:34 dev
drwxr-xr-x     0     0      4096 12-Jul-2008 14:34 home
drwxr-xr-x     0     0      4096 12-Jul-2008 14:34 initrd
drwxr-xr-x     0     0      4096 12-Jul-2008 14:34 lib
drwxr-xr-x     0     0      4096 12-Jul-2008 14:34 mnt
drwxr-xr-x     0     0      4096 12-Jul-2008 14:34 opt
drwxr-xr-x     0     0      4096 12-Jul-2008 14:34 proc
drwxr-xr-x     0     0      4096 12-Jul-2008 14:35 root
drwxr-xr-x     0     0      4096 12-Jul-2008 14:35 sbin
drwxr-xr-x     0     0      4096 12-Jul-2008 14:34 srv
drwxr-xr-x     0     0      4096 12-Jul-2008 14:34 sys
drwxrwxrwt     0     0      4096 12-Jul-2008 14:35 tmp
drwxr-xr-x     0     0      4096 12-Jul-2008 14:35 usr
lrwxrwxrwx     0     0        33 12-Jul-2008 14:34 initrd.img
lrwxrwxrwx     0     0        30 12-Jul-2008 14:34 vmlinuz

7.) Linux --> (This looks my lost file)
    =====
drwxr-xr-x     0     0      4096 15-Mar-2009 21:30 .
drwxr-xr-x     0     0      4096 15-Mar-2009 21:30 ..
drwx------     0     0     16384 13-Jul-2008 11:43 lost+found
drwxr-xr-x     0     0      4096  4-Jan-2009 06:40 var
drwxr-xr-x     0     0     12288  1-May-2009 21:13 etc
drwxr-xr-x     0     0      4096  1-May-2009 20:47 media
lrwxrwxrwx     0     0        11 13-Jul-2008 11:43 cdrom
drwxr-xr-x     0     0      4096 11-Mar-2009 04:18 bin
drwxr-xr-x     0     0      4096 16-Apr-2009 02:37 boot
drwxr-xr-x     0     0      4096 28-Feb-2009 08:29 dev
drwxr-xr-x     0     0      4096 26-Apr-2009 16:05 home
drwxr-xr-x     0     0      4096 16-Apr-2008 23:39 initrd
drwxr-xr-x     0     0     12288 30-Apr-2009 19:50 lib
drwxr-xr-x     0     0      4096 15-Apr-2008 05:53 mnt
drwxr-xr-x     0     0      4096 16-Apr-2008 23:39 opt
drwxr-xr-x     0     0      4096 15-Apr-2008 05:53 proc
drwxr-xr-x     0     0      4096  1-May-2009 19:45 root
drwxr-xr-x     0     0      4096 30-Apr-2009 19:50 sbin
drwxr-xr-x     0     0      4096 16-Apr-2008 23:39 srv
drwxr-xr-x     0     0      4096 14-Apr-2008 13:31 sys
drwxrwxrwt     0     0      4096  1-May-2009 21:13 tmp
drwxr-xr-x     0     0      4096 24-Mar-2009 05:27 usr
lrwxrwxrwx     0     0        33 28-Feb-2009 08:24 initrd.img
lrwxrwxrwx     0     0        30 28-Feb-2009 08:24 vmlinuz
-rw-r--r--     0     0       130 15-Mar-2009 21:30 .gtkwifi-dbg
-rw-r--r--  1000     0     28902  3-Jan-2007 05:35 .deb
lrwxrwxrwx     0     0        33 13-Jul-2008 05:55 initrd.img.old
lrwxrwxrwx     0     0        30 13-Jul-2008 05:55 vmlinuz.old

8.) Linux
    =====
No file found, filesystem seems damaged.

9.) Linux
    =====
No file found, filesystem seems damaged.

10.) Linux
     =====
No file found, filesystem seems damaged.

11.) Linux
     =====
No file found, filesystem seems damaged.

12.) Linux
     =====
No file found, filesystem seems damaged.

13.) Linux
     =====
No file found, filesystem seems damaged.     =====
```

I know that partition 7 is my lost partition because it has all the files I had in my "~/" and it has the user folders ("jerg" and "guest") in the home directory that I had .....I just want to know what to do now.....

Later,
Jerg

---

### Post by jerg on 2009-06-07
Thanks for all the help John, I just recovered my files and backed them up on my desktop. I'm now re-installing Windows and Ubuntu 9.04 ....sweeeeeet.

Thanks,
Jerg

---


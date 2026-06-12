---
title: "Problems with multi-booting - GRUB does not recognize Vista!"
date: 2009-01-24
forum: General Help
---

### Post by photon_man62 on 2009-01-24
Hello. So I bought myself a new computer without any OS, so I did this:

-Installed Vista.
-Used Vista for quite a while.
-Booted into GParted.
-Shrunk the Vista partition.
-Installed Windows XP on the unpartitioned space.
-Booted into the Ubuntu CD and unsuccessfully tried to install 2 times: froze at the final part at both times, so I booted into GParted each time and formatted and deleted the partitions, then made them again from the Ubuntu installer.
-Finally worked the 3rd time. Ubuntu runs smoothly.
-GRUB shows this:

Ubuntu kernel (something)
Ubuntu kernel (something) recovery mode
Ubuntu kernel (something else)
Ubuntu kernel (something else) recovery mode

Other operating systems:
Windows Vista/Longhorn

-Booted into Windows Vista/Longhorn and... guess what? XP showed up.

-------------------------

I NEED to be able to boot into Vista too, and I want to fix the OS names.

Any ideas?

---

### Post by photon_man62 on 2009-01-24
I would also like to add that I booted into GParted and flagged both Windows partitions with "boot".

---

### Post by caljohnsmith on 2009-01-24
Probably what happened is XP put its boot files in your Vista partition, and also modified the Vista boot sector to boot XP's "ntldr" rather than Vista's "bootmgr". That's one of the risks of installing XP after Vista, rather than vice-versa, but fortunately it can usually be fixed without too much fuss. In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by photon_man62 on 2009-01-25
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 sda1 ntfs-3g force 0 0

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda5 sda5 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda5 sda5 ntfs-3g force 0 0

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb5 sdb5 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb5 sdb5 ntfs-3g force 0 0

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1af91af8

Partition  Boot        Start          End         Size  Id System

/dev/sda1    *            63  576,653,174  576,653,112   7 HPFS/NTFS
/dev/sda2        576,653,175  976,751,999  400,098,825   f W95 Ext'd (LBA)
/dev/sda5    *   771,955,443  976,751,999  204,796,557   7 HPFS/NTFS
/dev/sda6        576,653,301  736,805,159  160,151,859  83 Linux
/dev/sda7        756,324,198  771,955,379   15,631,182  82 Linux swap / Solaris
/dev/sda8        736,805,223  756,324,134   19,518,912  83 Linux


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb37ee5a0

Partition  Boot        Start          End         Size  Id System

/dev/sdb1             16,065  488,392,064  488,376,000   f W95 Ext'd (LBA)
/dev/sdb5             16,128  488,392,064  488,375,937   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="12706D07706CF341" TYPE="ntfs" 
/dev/sda5: UUID="BA7868E37868A03D" TYPE="ntfs" 
/dev/sda6: UUID="e3f3440f-c893-49b7-bff8-c663b7290b69" TYPE="ext3" 
/dev/sda7: UUID="5d387c46-724c-444c-8b6c-9be459a8b426" TYPE="swap" 
/dev/sda8: UUID="102c51d0-21f0-4095-a6c2-f98b520dff8b" TYPE="ext3" 
/dev/sdb5: UUID="D234787434785D83" LABEL="HP Pocket Media Drive" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/dev/sda8 on /home type ext3 (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/aleksander/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=aleksander)

=========================== sda6/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=e3f3440f-c893-49b7-bff8-c663b7290b69 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e3f3440f-c893-49b7-bff8-c663b7290b69

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash apparmor.enabled=0 selinux=1

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		e3f3440f-c893-49b7-bff8-c663b7290b69
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=e3f3440f-c893-49b7-bff8-c663b7290b69 ro quiet splash apparmor.enabled=0 selinux=1 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		e3f3440f-c893-49b7-bff8-c663b7290b69
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=e3f3440f-c893-49b7-bff8-c663b7290b69 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		e3f3440f-c893-49b7-bff8-c663b7290b69
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e3f3440f-c893-49b7-bff8-c663b7290b69 ro quiet splash apparmor.enabled=0 selinux=1 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		e3f3440f-c893-49b7-bff8-c663b7290b69
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e3f3440f-c893-49b7-bff8-c663b7290b69 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		e3f3440f-c893-49b7-bff8-c663b7290b69
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sda6 :
UUID=e3f3440f-c893-49b7-bff8-c663b7290b69	/	ext3	relatime,errors=remount-ro	0	1
#Entry for /dev/sda8 :
UUID=102c51d0-21f0-4095-a6c2-f98b520dff8b	/home	ext3	relatime	0	2
#Entry for /dev/sda7 :
UUID=5d387c46-724c-444c-8b6c-9be459a8b426	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0
/dev/scd1	/media/cdrom1	udf,iso9660	user,noauto,exec,utf8	0	0



=================== sda6: Location  of files loaded by Grub: ===================


 311.6GB: boot/grub/menu.lst
 311.6GB: boot/grub/stage2
 311.7GB: boot/initrd.img-2.6.27-7-generic
 311.7GB: boot/initrd.img-2.6.27-9-generic
 311.7GB: boot/vmlinuz-2.6.27-7-generic
 311.7GB: boot/vmlinuz-2.6.27-9-generic
 311.7GB: initrd.img
 311.7GB: initrd.img.old
 311.7GB: vmlinuz
 311.7GB: vmlinuz.old

=======Devices which don't seem to have a corresponding hard drive==============

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-25
OK, how about doing:
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
sudo ntfsfix /dev/sda5
sudo mkdir /mnt/sda{1,5}
sudo mount /dev/sda1 /mnt/sda1 && ls -l /mnt/sda1
sudo mount /dev/sda5 /mnt/sda5 && ls -l /mnt/sda5
```
Please post the output of all the above commands. Also, do you you have a Vista Install CD? You'll need that since XP overwrote your Vista boot sector.

---

### Post by photon_man62 on 2009-01-25
Yes, I have the Vista install CD.

So I tried to install ntfsprogs but it said  I should type in apt-get autoremove. I did that, and installed again. Then I seem to get this:

```
aleksander@aleksander-desktop:~$ apt-get install ntfsprogs
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
aleksander@aleksander-desktop:~$ sudo apt-get install ntfsprogs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfsprogs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
aleksander@aleksander-desktop:~$ sudo ntfsfix /dev/sda1
**sudo: ntfsfix: command not found**
aleksander@aleksander-desktop:~$
```

---

### Post by photon_man62 on 2009-01-25
Never mind, I removed ntfsprogs and installed it again. Now I get this:

```
aleksander@aleksander-desktop:~$ sudo ntfsfix /dev/sda1
[sudo] password for aleksander: 
sudo: ntfsfix: command not found
aleksander@aleksander-desktop:~$ sudo apt-get remove ntfsprogs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ntfsprogs ubiquity ubiquity-frontend-gtk
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 10.7MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 162505 files and directories currently installed.)
Removing ubiquity ...
Removing ubiquity-frontend-gtk ...
Removing ntfsprogs ...
Processing triggers for man-db ...
aleksander@aleksander-desktop:~$ sudo apt-get install ntfsprogs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  ntfsprogs
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 269kB of archives.
After this operation, 688kB of additional disk space will be used.
Get:1 [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) intrepid/main ntfsprogs 2.0.0-1ubuntu2 [269kB]
Fetched 269kB in 2s (118kB/s)     
Selecting previously deselected package ntfsprogs.
(Reading database ... 161961 files and directories currently installed.)
Unpacking ntfsprogs (from .../ntfsprogs_2.0.0-1ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up ntfsprogs (2.0.0-1ubuntu2) ...
aleksander@aleksander-desktop:~$ sudo ntfsfix /dev/sda1
**ntfsfix: error while loading shared libraries: libntfs.so.10: cannot open shared object file: No such file or directory**
aleksander@aleksander-desktop:~$ sudo ntfsfix /dev/sda1
**ntfsfix: error while loading shared libraries: libntfs.so.10: cannot open shared object file: No such file or directory**
aleksander@aleksander-desktop:~$
```

---

### Post by caljohnsmith on 2009-01-25
OK, how about posting:
```
apt-cache policy ntfsprogs
ls -l /usr/bin/ntfs*
which ntfsfix
echo $PATH
```

---

### Post by photon_man62 on 2009-01-25
```
aleksander@aleksander-desktop:~$ apt-cache policy ntfsprogs
ntfsprogs:
  Installed: 2.0.0-1ubuntu2
  Candidate: 2.0.0-1ubuntu2
  Version table:
 *** 2.0.0-1ubuntu2 0
        500 http://pl.archive.ubuntu.com intrepid/main Packages
        100 /var/lib/dpkg/status
aleksander@aleksander-desktop:~$ ls -l /usr/bin/ntfs*
-rwxr-xr-x 1 root root 22256 2008-02-24 09:22 /usr/bin/ntfscat
-rwxr-xr-x 1 root root 27696 2008-02-24 09:22 /usr/bin/ntfscluster
-rwxr-xr-x 1 root root 26476 2008-02-24 09:22 /usr/bin/ntfscmp
-rwxr-xr-x 1 root root 24424 2008-02-24 09:22 /usr/bin/ntfsfix
-rwxr-xr-x 1 root root 47360 2008-02-24 09:22 /usr/bin/ntfsinfo
-rwxr-xr-x 1 root root 24508 2008-02-24 09:22 /usr/bin/ntfsls
-rwxr-xr-x 1 root root 39120 2008-02-24 09:22 /usr/bin/ntfsmount
aleksander@aleksander-desktop:~$ which ntfsfix
/usr/bin/ntfsfix
aleksander@aleksander-desktop:~$ echo $PATH
/home/aleksander/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
aleksander@aleksander-desktop:~$ 

```

---

### Post by caljohnsmith on 2009-01-25
Something seems to be wrong with your libraries, how about trying:
```
sudo apt-get purge libntfs10
sudo apt-get install libntfs10
```
And then try running ntfsfix again.

---

### Post by photon_man62 on 2009-01-25
OK, seems to work now. (as in the command, not Vista)
```

aleksander@aleksander-desktop:~$ sudo ntfsfix /dev/sda1
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sda1 was processed successfully.
aleksander@aleksander-desktop:~$ sudo ntfsfix /dev/sda5
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sda5 was processed successfully.
aleksander@aleksander-desktop:~$ sudo mkdir /mnt/sda{1,5}
aleksander@aleksander-desktop:~$ sudo mount /dev/sda1 /mnt/sda1 && ls -l /mnt/sda1
total 3145663
-rwxrwxrwx 1 root root         24 2006-09-18 23:43 autoexec.bat
drwxrwxrwx 1 root root       4096 2009-01-22 23:19 Boot
-rwxrwxrwx 1 root root        211 2009-01-24 01:05 boot.ini
-rwxrwxrwx 1 root root     333203 2008-01-19 08:45 bootmgr
-rwxrwxrwx 1 root root       8192 2009-01-20 04:35 BOOTSECT.BAK
-rwxrwxrwx 3 root root         10 2006-09-18 23:43 config.sys
drwxrwxrwx 1 root root          0 2006-11-02 14:00 Documents and Settings
-rwxrwxrwx 1 root root 3220430848 2009-01-23 14:52 hiberfil.sys
drwxrwxrwx 1 root root          0 2009-01-22 23:12 inetpub
drwxrwxrwx 1 root root          0 2009-01-19 19:55 Intel
-rwxrwxrwx 1 root root          0 2009-01-22 21:59 IO.SYS
-rwxrwxrwx 1 root root          0 2009-01-22 21:59 MSDOS.SYS
-rwxrwxrwx 1 root root      47564 2008-04-14 10:00 NTDETECT.COM
-rwxrwxrwx 1 root root     250048 2008-04-14 10:00 ntldr
drwxrwxrwx 1 root root          0 2009-01-21 08:35 NVIDIA
drwxrwxrwx 1 root root          0 2009-01-22 23:12 PerfLogs
drwxrwxrwx 1 root root       4096 2009-01-24 00:14 ProgramData
drwxrwxrwx 1 root root      12288 2009-01-24 00:32 Program Files
drwxrwxrwx 1 root root          0 2009-01-19 19:45 $Recycle.Bin
-rwxrwxrwx 1 root root        159 2009-01-19 20:10 Setup.log
drwxrwxrwx 1 root root      20480 2009-01-24 01:14 System Volume Information
-rwxrwxrwx 1 root root         11 2009-01-23 23:41 trace.ini
drwxrwxrwx 1 root root       4096 2009-01-19 19:45 Users
drwxrwxrwx 1 root root      32768 2009-01-24 00:38 Windows
aleksander@aleksander-desktop:~$ sudo mount /dev/sda5 /mnt/sda5 && ls -l /mnt/sda5
total 2095152
drwxrwxrwx 1 root root       4096 2009-01-24 01:14 Documents and Settings
drwxrwxrwx 1 root root          0 2009-01-24 22:40 Intel
-rwxrwxrwx 1 root root 2145386496 2009-01-25 10:38 pagefile.sys
drwxrwxrwx 1 root root       8192 2009-01-24 22:40 Program Files
drwxrwxrwx 1 root root       4096 2009-01-24 01:14 System Volume Information
drwxrwxrwx 1 root root      32768 2009-01-24 22:44 WINDOWS
aleksander@aleksander-desktop:~$ 

```

---

### Post by caljohnsmith on 2009-01-25
OK, as I suspected, Windows XP put its boot files in your Vista partition and modified the Vista boot sector to boot XP's "ntldr" rather than Vista's "bootmgr". To get Vista and XP booting separately, how about first doing the following while you still have sda1 and sda5 mounted in the /mnt directory:
```
sudo mv /mnt/sda1/boot.ini /mnt/sda1/ntldr /mnt/sda1/NTDETECT.COM /mnt/sda5
gksudo gedit /mnt/sda5/boot.ini
```
And check that your boot.ini file uses "partition(2)" in both places:
```

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)[COLOR="Blue"]partition(2)[/COLOR]\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)[COLOR="Blue"]partition(2)[/COLOR]\WINDOWS="Microsoft Windows XP" /fastdetect /NoExecute=OptIn

```
Then open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And add the following entry at the bottom:
```
title Windows XP
rootnoverify (hd0,4)
chainloader +1
```
And then you will also need to repair the XP boot sector with "testdisk", so first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "No log", choose the correct HDD and "Proceed", choose "Intel", choose "Advanced", select the Windows XP sda5 partition (not the sda1 Vista partition), choose "Boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". After you are done doing the "Rebuild BS" in testdisk, reboot and let me know exactly what happens when you boot Windows XP from the Grub menu. Also, to fix your Vista install, how about booting your Vista Install CD, go to the command line and run:
```
bootrec /fixboot
```
And then try booting Vista from your Grub menu, and let me know exactly what happens. We can work from there.

---

### Post by photon_man62 on 2009-01-25
OK, so I booted "Windows XP" from GRUB and XP booted successfully. It ran 2 disk checks and rebooted the computer. I booted into XP again, and it booted successfully to the desktop.

Now I'll boot into the Vista CD and repair the boot manager (or whatever).

---

### Post by photon_man62 on 2009-01-25
Yes! It works! I booted into "Windows Vista/Longhorn (loader)" and Vista popped up! Thank you so much for your patience in typing all this stuff. I'll never forget this. Thank you!

:D:D:D

---

### Post by caljohnsmith on 2009-01-25
Glad that did the trick; cheers and enjoy Vista, XP, and Ubuntu. :)

---

### Post by photon_man62 on 2009-01-25
> **caljohnsmith said:**
> Glad that did the trick; cheers and enjoy Vista, XP, and Ubuntu. :)

Right!

Thanks again!

He he he

Vista = games and some apps
XP = older games and apps
Ubuntu = work and relaxing (internet, IMing, office suites)

---


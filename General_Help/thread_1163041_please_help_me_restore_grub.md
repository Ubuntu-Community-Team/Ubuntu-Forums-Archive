---
title: "please help me restore grub"
date: 2009-05-18
forum: General Help
---

### Post by wendallsan on 2009-05-18
Hi all,

I have several OS's on partitions on my computer, and yesterday installed WinXP on my hda4 partition.  I expected XP to overwrite my grub bootload on the MBR, and was planning to just restore grub and then chainload windows from grub.

I think my install didn't succeed, and now when I boot I get the message "invalid partition table".

I've booted to my liveCD and have found a thread about this on this forum ([http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub+live+ubuntu+cd](http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub+live+ubuntu+cd)), but the instructions in those threads don't seem to work . . . 

Their instructions and grub's output:

```

grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd1,0)
 (hd1,1)
 (hd1,5)

```

I want to run grub from my hda6 (hd0,5 in grub) partition, which is being shown here as hdb6 (hd1,5) when I boot from my liveCD.

I try to set up this partition in grub:

```

grub> root (hd1,5)
root (hd1,5)

```

Then I try to set up grub on the MBR, which I'm fairly certain will always be hd0 even if my liveCD messes with my 'normal' disk layout and thinks of hd0 as hd1.

```

grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd1,5)/boot/grub/stage2 /boot/grub/menu.lst"... failed

Error 22: No such partition

```

In desparation, I've tried to 'setup (hd1)':

```

grub> setup (hd1)
setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd1) (hd0)1+15 p (hd1,5)/boot/grub/stage2 /boot/grub/menu.lst"... failed

Error 22: No such partition

```

So either way my install /boot/grub/stage1 fails.

Can anyone help me figure out what has happened here?  Thanks for any help!

---

### Post by Brandon Williams on 2009-05-18
Oh no! You finally had all of the Linux installations working as expected and now you brought windows to the party! ... ouch!!

It sounds like the attempted windows install might have screwed up your partition table. From the live distro, run 'sudo fdisk -l /dev/hdb' (it might be /dev/sdb instead, depending on the disk type). Does fdisk give you the correct information about all of your partitions? Next, try mounting the partitions. Are you able to mount all of them? If fdisk doesn't tell you the right information and/or you can't mount them, then you might have to reconstruct your partition table.

You probably also want to run the bootinfo script that you used for one of your previous threads so that we can see exactly what things look like now. The extra info could help us to make better suggestions.

I just saw a different post that seemed like it might be similar. The OP had trouble with ext3 partitions that appeared to be the result of some work in windows. He ran fsck on the ext3 filesystems and his problems were solved. Perhaps you want to try running fsck on your /dev/hdb6 from within the live CD environment and then attempt to install grub again.

Oh, and one more note, if grub sees the partition on the main hard drive as hd(1,5), then you do indeed want to intall grub to hd(1), not hd(0). You menu.lst for on /dev/hdb6 should still refer to the drive as hd(0) though, since it will be /dev/hda when you aren't in the live CD environment.

---

### Post by wendallsan on 2009-05-18
Hi, the output from boot_info_script is below.  I am able to mount all my partitions, so it looks like my partition table may not be boned after all.  I'll try the fsck command later today and let you know how that goes.  Thanks again!

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #256 for /boot/grub/stage2.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux 4.0
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x48ee87dc

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,768,064   976,768,002  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x14cb14cb

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   185,839,919   185,839,857  83 Linux
/dev/sdb2         185,839,920   288,238,229   102,398,310  83 Linux
/dev/sdb3    *    288,238,230   390,636,539   102,398,310   7 HPFS/NTFS
/dev/sdb4    *    390,636,540   488,392,064    97,755,525   5 Extended
/dev/sdb5         390,636,666   483,106,679    92,470,014  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="dea26dd4-d38d-4fa9-9f7a-b21cfbfac36c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="d6a09043-40e9-4faa-a16f-eaadd3e3790c" TYPE="ext3" 
/dev/sdb2: UUID="d86fa4e9-1084-45e7-8f38-57b503e7eefd" TYPE="ext3" 
/dev/sdb3: UUID="24503FBF503F9710" TYPE="ntfs" 
/dev/sdb5: UUID="3b188cc9-42c9-4ae8-ae39-f36260a52c09" TYPE="ext3" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/1 type ext3 (rw)
/dev/sdb2 on /media/2 type ext3 (rw)
/dev/sdb5 on /media/5 type ext3 (rw)
/dev/sdb3 on /media/3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sdb1/boot/grub/menu.lst: ===========================

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
default		4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
# defoptions=quiet splash

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

#title		Ubuntu 8.04.1, kernel 2.6.24.7-rt25-custom
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24.7-rt25-custom root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro quiet splash
#initrd		/boot/initrd.img-2.6.24.7-rt25-custom
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24.7-rt25-custom (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24.7-rt25-custom root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro single
#initrd		/boot/initrd.img-2.6.24.7-rt25-custom

#title		Ubuntu 8.04.1, kernel 2.6.24.7-rt25
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24.7-rt25 root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro quiet splash
#initrd		/boot/initrd.img-2.6.24.7-rt25
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24.7-rt25 (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24.7-rt25 root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro single
#initrd		/boot/initrd.img-2.6.24.7-rt25

#title		Ubuntu 8.04.1, kernel 2.6.24-23-rt
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-23-rt root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro quiet splash
#initrd		/boot/initrd.img-2.6.24-23-rt
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-23-rt (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-23-rt root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro single
#initrd		/boot/initrd.img-2.6.24-23-rt


####################################
# THIS IS GENERIC UBUNTU KERNEL
####################################

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro single
initrd		/boot/initrd.img-2.6.24-23-generic

##################################
# THIS IS THE UBUNTU STUDIO KERNEL??
##################################

title		Ubuntu 8.04.1, kernel 2.6.24-22-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-rt root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-rt
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-rt root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro single
initrd		/boot/initrd.img-2.6.24-22-rt

#title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro quiet splash
#initrd		/boot/initrd.img-2.6.24-22-generic
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro single
#initrd		/boot/initrd.img-2.6.24-22-generic

#title		Ubuntu 8.04.1, kernel 2.6.24-21-rt
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-21-rt root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro quiet splash
#initrd		/boot/initrd.img-2.6.24-21-rt
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-21-rt (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-21-rt root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro single
#initrd		/boot/initrd.img-2.6.24-21-rt

#title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro quiet splash
#initrd		/boot/initrd.img-2.6.24-21-generic
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro single
#initrd		/boot/initrd.img-2.6.24-21-generic

#itle		Ubuntu 8.04.1, kernel 2.6.24-19-generic
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro quiet splash
#initrd		/boot/initrd.img-2.6.24-19-generic
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro single
#initrd		/boot/initrd.img-2.6.24-19-generic

#title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro quiet splash
#initrd		/boot/initrd.img-2.6.24-18-generic
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro single
#initrd		/boot/initrd.img-2.6.24-18-generic

#title		Ubuntu 8.04.1, kernel 2.6.24-17-generic
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro quiet splash
#initrd		/boot/initrd.img-2.6.24-17-generic
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-17-generic (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro single
#initrd		/boot/initrd.img-2.6.24-17-generic

#title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro quiet splash
#initrd		/boot/initrd.img-2.6.24-16-generic
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro single
#initrd		/boot/initrd.img-2.6.24-16-generic

#title		Ubuntu 8.04.1, memtest86+
#root		(hd0,0)
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sde1
UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sde5
UUID=99998326-dc28-4a49-b466-2afce77293e2 none            swap    sw              0       0
# /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  78.3GB: boot/grub/menu.lst
  69.7GB: boot/grub/stage2
  69.8GB: boot/initrd.img-2.6.24-16-generic
  69.9GB: boot/initrd.img-2.6.24-16-generic.bak
  69.9GB: boot/initrd.img-2.6.24-17-generic
  69.9GB: boot/initrd.img-2.6.24-17-generic.bak
  13.6GB: boot/initrd.img-2.6.24-18-generic
  73.7GB: boot/initrd.img-2.6.24-18-generic.bak
  13.6GB: boot/initrd.img-2.6.24-19-generic
  13.6GB: boot/initrd.img-2.6.24-19-generic.bak
  69.8GB: boot/initrd.img-2.6.24-21-generic
  69.9GB: boot/initrd.img-2.6.24-21-generic.bak
  69.9GB: boot/initrd.img-2.6.24-21-rt
  69.9GB: boot/initrd.img-2.6.24-21-rt.bak
  69.8GB: boot/initrd.img-2.6.24-22-generic
  69.9GB: boot/initrd.img-2.6.24-22-generic.bak
  69.8GB: boot/initrd.img-2.6.24-22-rt
  69.9GB: boot/initrd.img-2.6.24-22-rt.bak
  70.0GB: boot/initrd.img-2.6.24-23-generic
  77.2GB: boot/initrd.img-2.6.24-23-generic.bak
  77.2GB: boot/initrd.img-2.6.24-23-rt
  70.0GB: boot/initrd.img-2.6.24-23-rt.bak
  69.8GB: boot/initrd.img-2.6.24.7-rt25
  70.0GB: boot/initrd.img-2.6.24.7-rt25-custom
  69.9GB: boot/vmlinuz-2.6.24-16-generic
  69.8GB: boot/vmlinuz-2.6.24-17-generic
  13.5GB: boot/vmlinuz-2.6.24-18-generic
  13.5GB: boot/vmlinuz-2.6.24-19-generic
  69.8GB: boot/vmlinuz-2.6.24-21-generic
  69.8GB: boot/vmlinuz-2.6.24-21-rt
  69.8GB: boot/vmlinuz-2.6.24-22-generic
  69.8GB: boot/vmlinuz-2.6.24-22-rt
  77.2GB: boot/vmlinuz-2.6.24-23-generic
  70.0GB: boot/vmlinuz-2.6.24-23-rt
  69.9GB: boot/vmlinuz-2.6.24.7-rt25
  69.8GB: boot/vmlinuz-2.6.24.7-rt25-custom
  77.2GB: initrd.img
  70.0GB: initrd.img.old
  70.0GB: vmlinuz
  77.2GB: vmlinuz.old

=========================== sdb2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=d86fa4e9-1084-45e7-8f38-57b503e7eefd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d86fa4e9-1084-45e7-8f38-57b503e7eefd

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
# defoptions=quiet splash

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		d86fa4e9-1084-45e7-8f38-57b503e7eefd
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d86fa4e9-1084-45e7-8f38-57b503e7eefd ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		d86fa4e9-1084-45e7-8f38-57b503e7eefd
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d86fa4e9-1084-45e7-8f38-57b503e7eefd ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		d86fa4e9-1084-45e7-8f38-57b503e7eefd
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro single 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-22-rt (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-22-rt root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro quiet splash 
initrd		/boot/initrd.img-2.6.24-22-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-22-rt (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-22-rt root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro single 
initrd		/boot/initrd.img-2.6.24-22-rt
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb3
title		Windows NT/2000/XP (loader)
rootnoverify	(hd1,2)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		64studio, kernel 2.6.21-1-multimedia-amd64 (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.21-1-multimedia-amd64 root=/dev/hda6 ro vga=791 splash=silent 
initrd		/boot/initrd.img-2.6.21-1-multimedia-amd64
savedefault
boot


=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=d86fa4e9-1084-45e7-8f38-57b503e7eefd /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


 113.8GB: boot/grub/menu.lst
 113.8GB: boot/grub/stage2
 113.8GB: boot/initrd.img-2.6.28-11-generic
 113.9GB: boot/vmlinuz-2.6.28-11-generic
 113.8GB: initrd.img
 113.9GB: vmlinuz

================================ sdb3/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS.2

[operating systems]

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS.2="Microsoft Windows XP Professional" /fastdetect /noexecute=optin

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS.1="Microsoft Windows XP Professional" /fastdetect /noexecute=optin

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS.0="Microsoft Windows XP Professional" /fastdetect /noexecute=optin

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin


=========================== sdb5/boot/grub/menu.lst: ===========================

default		0
timeout 	10
color cyan/blue white/blue

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
# kopt=root=/dev/hda6 ro vga=791 splash=silent

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
# defoptions=

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

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

### END DEBIAN AUTOMAGIC KERNELS LIST

title		64studio, kernel 2.6.21-1-multimedia-amd64
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.21-1-multimedia-amd64 root=/dev/hda6 ro vga=791 splash=silent 
initrd		/boot/initrd.img-2.6.21-1-multimedia-amd64
savedefault

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot

# NOW AN ATTEMPT TO GET UBUNTU 9:

title Ubuntu 9.04, kernel 2.6.24-21-generic
uuid 04bdb9ab-fd31-472f-a19c-092d0bfca72f
kernel /boot/vmlinuz-2.6.28-11-generic ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic
quiet

title Chainload to Ubuntu 9.04
root (hd0,2)
chainloader +1

# COPIED FROM THE UBU 9.04 PARTITION BOOTLOADER FOR REFERENCE
# title		Ubuntu 9.04, kernel 2.6.28-11-generic
# root		(hd0,4)
# uuid		04bdb9ab-fd31-472f-a19c-092d0bfca72f
# kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=04bdb9ab-fd31-472f-a19c-092d0bfca72f ro quiet splash 
# initrd		/boot/initrd.img-2.6.28-11-generic
# quiet

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1	/media/Nyo	ext3	user   0	0
# MODIFIED TO ALLOW WRITE PRIVELEGES (doesn't work yet)
# /dev/sda1	/media/Nyo	ntfs-3g	defaults,locale=en_US.utf8   0    0



=================== sdb5: Location of files loaded by Grub: ===================


 211.0GB: boot/grub/menu.lst
 211.0GB: boot/grub/stage2
 211.1GB: boot/initrd.img-2.6.21-1-multimedia-amd64
 211.0GB: boot/initrd.img-2.6.21-1-multimedia-amd64.bak
 211.0GB: boot/vmlinuz-2.6.21-1-multimedia-amd64
 211.1GB: initrd.img
 211.0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

```

---

### Post by wendallsan on 2009-05-18
Hi again,

Here's my results from using fsck:

```

sudo fsck -t ext3 /dev/sdb5
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sdb5: clean, 253777/5727072 files, 11096474/11558751 blocks

```

I went ahead and ran fsck on all my linux partitions and they all had similar results (clean).

I tried to set up grub again and got the same result:

```

grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd1,0)
 (hd1,1)
 (hd1,5)
grub> root (hd1,5)
root (hd1,5)
grub> setup (hd1)
setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+15 p (hd1,5)/boot/grub/stage2 /boot/grub/menu.lst"... failed

Error 22: No such partition

```

Any further ideas or suggestions?  I appreciate all help!

---

### Post by Brandon Williams on 2009-05-19
I think that the windows install screwed up your partition table. It used to look like this (from a previous thread):
```
Drive: hda ___________________ _____________________________________________________

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/hda1                  63   185,839,919   185,839,857  83 Linux
/dev/hda2    *    390,636,540   488,392,064    97,755,525   5 Extended
/dev/hda5         483,106,743   488,392,064     5,285,322  82 Linux swap / Solaris
/dev/hda6         390,636,666   483,106,679    92,470,014  83 Linux
/dev/hda3         185,839,920   288,238,229   102,398,310  83 Linux
/dev/hda4         288,238,230   390,636,539   102,398,310   7 HPFS/NTFS

```

Now it looks like this:
```
Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x14cb14cb

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   185,839,919   185,839,857  83 Linux
/dev/sdb2         185,839,920   288,238,229   102,398,310  83 Linux
/dev/sdb3    *    288,238,230   390,636,539   102,398,310   7 HPFS/NTFS
/dev/sdb4    *    390,636,540   488,392,064    97,755,525   5 Extended
/dev/sdb5         390,636,666   483,106,679    92,470,014  83 Linux

```

Bearing in mind that /dev/hda in the previous example is /dev/sdb in this example (I think).

One important thing of note is that you have lost your swap partition in the process. You will definitely want to use fdisk to put that back.

You might also want to restore the partition table entirely to what it looked like before so that all of your partition numbers are restored to their previous values. You have to be very careful when you do it to make sure that each partition starts and stops at exactly the same place that it did before. If you do that, then the grub command you're trying to run should work, and all of your previous linux installations should work. 

I don't know if XP can handle such a change, though, since it believes that it was installed to /dev/hda3 at this point. It may be that windows wants the extended partition to come after all of the primary partitions, in which case you won't be able to put the partition table back the way it was. However, you _might_ be able to get it to work by restoring the original partition table, but with /dev/hda2 and /dev/hda4 swapped ... call the NTFS partition number 2 and the extended partition number 4, but make all the others match their previous numbers.

If windows won't boot using the restored partition table or the suggested alternate, then you'll have to put it back the way it is now and manually edit all of the grub menu.lst files and /etc/fstab files to make sure that all of the partitions are referred to by their new partition numbers.

---


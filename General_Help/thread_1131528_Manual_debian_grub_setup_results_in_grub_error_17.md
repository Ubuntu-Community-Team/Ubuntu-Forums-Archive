---
title: "Manual debian grub setup results in grub error 17"
date: 2009-04-20
forum: General Help
---

### Post by dragos240 on 2009-04-20
Hello all!

I copied my grub folder to my debian partition because when installing debian I chose to do this manually. Also since the partition was on my third drive on the second partition, I did this,

root (hd2,1)

setup (hd2)

Is this right?

Grub boots fine, but when I ask for grub to boot debian it just says it can't mount the selected partition. Why is this? By the way, I installed debian inside my usb drive.

---

### Post by codeseer on 2009-04-20
Results.txt please.

[http://sourceforge.net/projects/bootinfoscript/]("http://sourceforge.net/projects/bootinfoscript/")

---

### Post by dragos240 on 2009-04-20
> **codeseer said:**
> Results.txt please.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Okay.
```

============================= Boot Info Summary: ==============================

 => Grub2 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdi and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 sda2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 sda2 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 sda2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 sda2 ntfs-3g force 0 0

sda3: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda3 and 
                       looks at sector 277136102 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdi1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdi2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux 4.0
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0a7d030c

Partition  Boot         Start           End          Size  Id System

/dev/sda1         535,012,695   625,137,344    90,124,650  83 Linux
/dev/sda2    *             63   273,072,869   273,072,807   7 HPFS/NTFS
/dev/sda3         273,072,870   535,012,694   261,939,825  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e4dce

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   519,381,449   519,381,387  83 Linux
/dev/sdb2         965,394,045   976,768,064    11,374,020   5 Extended
/dev/sdb5         965,394,108   976,768,064    11,373,957  82 Linux swap / Solaris
/dev/sdb3         519,381,450   965,394,044   446,012,595  83 Linux


Drive: sdi ___________________ _____________________________________________________

Disk /dev/sdi: 32.3 GB, 32346472448 bytes
255 heads, 63 sectors/track, 3932 cylinders, total 63176704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04dd5721

Partition  Boot         Start           End          Size  Id System

/dev/sdi1                  63     3,325,454     3,325,392   c W95 FAT32 (LBA)
/dev/sdi2    *      3,325,455    63,167,579    59,842,125  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="06c8d4c4-4561-41b5-ba24-004cd95d7e99" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="2020202020202020" TYPE="ntfs" 
/dev/sda3: UUID="07446460-fa38-4d28-bf91-23ef304158d1" TYPE="ext2" 
/dev/sdb1: UUID="4eafc17c-1a55-45b9-be42-c26398ba0d7b" TYPE="ext3" 
/dev/sdb3: UUID="f72049b3-d2e4-4cc9-88f8-a8a35b7cc604" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="032ac103-720b-4d7a-81ac-591380c5a525" TYPE="swap" 
/dev/sdi1: LABEL="CORSAIR" UUID="167A-4B4F" TYPE="vfat" 
/dev/sdi2: UUID="fdf2f680-3dfe-40a2-b726-cd9b2ce86c85" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/harley/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=harley)
/dev/sdi1 on /media/CORSAIR type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdi2 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=07446460-fa38-4d28-bf91-23ef304158d1 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=4959-0F92  /dos            vfat    utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=7036A1F436A1BB8A /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=90519367-f00e-40f8-9a19-b6f62525dc1f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 142.5GB: boot/initrd.img-2.6.27-11-generic
 142.0GB: boot/initrd.img-2.6.27-7-generic
 141.9GB: boot/initrd.img-2.6.27-9-generic
 142.4GB: boot/vmlinuz-2.6.27-11-generic
 141.8GB: boot/vmlinuz-2.6.27-7-generic
 141.8GB: boot/vmlinuz-2.6.27-9-generic
 142.5GB: initrd.img
 141.9GB: initrd.img.old
 142.4GB: vmlinuz
 141.8GB: vmlinuz.old

=========================== sdb1/boot/grub/menu.lst: ===========================

splashimage=(hd1,0)/home/harley/Desktop/splash.xpm.gz
default 0
timeout 10

title Debian GNU/Linux, kernel 2.6.27-11-generic
root 4eafc17c-1a55-45b9-be42-c26398ba0d7b
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=4eafc17c-1a55-45b9-be42-c26398ba0d7b ro quiet splash
initrd /boot/initrd.img-2.6.27-11-generic

title Debian GNU/Linux, kernel 2.6.27-11-generic (recovery mode)
root 4eafc17c-1a55-45b9-be42-c26398ba0d7b
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=4eafc17c-1a55-45b9-be42-c26398ba0d7b ro single
initrd /boot/initrd.img-2.6.27-11-generic

title Debian GNU/Linux, kernel 2.6.27-7-generic
root 4eafc17c-1a55-45b9-be42-c26398ba0d7b
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=4eafc17c-1a55-45b9-be42-c26398ba0d7b ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic

title Debian GNU/Linux, kernel 2.6.27-7-generic (recovery mode)
root 4eafc17c-1a55-45b9-be42-c26398ba0d7b
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=4eafc17c-1a55-45b9-be42-c26398ba0d7b ro single
initrd /boot/initrd.img-2.6.27-7-generic

title Debian GNU/Linux, kernel memtest86+
root 4eafc17c-1a55-45b9-be42-c26398ba0d7b
kernel /boot/memtest86+.bin

title Other operating systems:
root 

title Windows Vista/Longhorn (loader)
root (hd0,1)
chainloader +1
savedefault
makeactive

title Ubuntu 8.10 (8.10) (on /dev/sda3)
root (hd0,2)
kernel /boot/vmlinuz-2.6.27-11-generic root=/dev/sda3
initrd /boot/initrd.img-2.6.27-11-generic
savedefault

title Ubuntu 8.10 (8.10) (on /dev/sda3)
root (hd0,2)
kernel /boot/vmlinuz-2.6.27-7-generic root=/dev/sda3
initrd /boot/initrd.img-2.6.27-7-generic
savedefault

title Ubuntu 8.10 (8.10) (on /dev/sda3)
root (hd0,2)
kernel /boot/vmlinuz-2.6.27-9-generic root=/dev/sda3
initrd /boot/initrd.img-2.6.27-9-generic
savedefault
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
# kopt=root=/dev/sdb1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Debian GNU/Linux, kernel 2.6.27-11-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.27-11-generic root=/dev/sdb1 ro 
initrd        /boot/initrd.img-2.6.27-11-generic

title        Debian GNU/Linux, kernel 2.6.27-11-generic (single-user mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.27-11-generic root=/dev/sdb1 ro single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Debian GNU/Linux, kernel 2.6.27-7-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.27-7-generic root=/dev/sdb1 ro 
initrd        /boot/initrd.img-2.6.27-7-generic

title        Debian GNU/Linux, kernel 2.6.27-7-generic (single-user mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.27-7-generic root=/dev/sdb1 ro single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Debian GNU/Linux, kernel memtest86+
root        (hd1,0)
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/update-grub using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
set default=0
set timeout=5
set root=(hd1,1)
if font (hd1,1)/usr/share/grub/unicode.pff ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  terminal gfxterm
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_hurd ###
### END /etc/grub.d/10_hurd ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, linux 2.6.27-7-generic" {
    linux    (hd1,1)/boot/vmlinuz-2.6.27-7-generic root=UUID=4eafc17c-1a55-45b9-be42-c26398ba0d7b ro quiet splash 
    initrd    (hd1,1)/boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu, linux 2.6.27-7-generic (single-user mode)" {
    linux    (hd1,1)/boot/vmlinuz-2.6.27-7-generic root=UUID=4eafc17c-1a55-45b9-be42-c26398ba0d7b ro single
    initrd    (hd1,1)/boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu, linux 2.6.27-11-generic" {
    linux    (hd1,1)/boot/vmlinuz-2.6.27-11-generic root=UUID=4eafc17c-1a55-45b9-be42-c26398ba0d7b ro quiet splash 
    initrd    (hd1,1)/boot/initrd.img-2.6.27-11-generic
}
menuentry "Ubuntu, linux 2.6.27-11-generic (single-user mode)" {
    linux    (hd1,1)/boot/vmlinuz-2.6.27-11-generic root=UUID=4eafc17c-1a55-45b9-be42-c26398ba0d7b ro single
    initrd    (hd1,1)/boot/initrd.img-2.6.27-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux    (hd1,1)/boot/memtest86+.bin
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista/Longhorn (loader) (on /dev/sda2)" {
    set root=(hd0,2)
    chainloader +1
}
menuentry "Ubuntu 8.10 (8.10) (on /dev/sda3)" {
    set root=(hd0,3)
    linux /boot/vmlinuz-2.6.27-11-generic root=/dev/sda3
    initrd /boot/initrd.img-2.6.27-11-generic
}
menuentry "Ubuntu 8.10 (8.10) (on /dev/sda3)" {
    set root=(hd0,3)
    linux /boot/vmlinuz-2.6.27-7-generic root=/dev/sda3
    initrd /boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu 8.10 (8.10) (on /dev/sda3)" {
    set root=(hd0,3)
    linux /boot/vmlinuz-2.6.27-9-generic root=/dev/sda3
    initrd /boot/initrd.img-2.6.27-9-generic
}
### END /etc/grub.d/30_os-prober ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=4eafc17c-1a55-45b9-be42-c26398ba0d7b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=032ac103-720b-4d7a-81ac-591380c5a525 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   5.2GB: boot/grub/grub.cfg
   5.3GB: boot/grub/menu.lst
   5.2GB: boot/initrd.img-2.6.27-11-generic
   5.3GB: boot/initrd.img-2.6.27-7-generic
   5.2GB: boot/vmlinuz-2.6.27-11-generic
   5.3GB: boot/vmlinuz-2.6.27-7-generic
   5.2GB: initrd.img
   5.3GB: initrd.img.old
   5.2GB: vmlinuz
   5.3GB: vmlinuz.old

=========================== sdi2/boot/grub/menu.lst: ===========================

default 0
timeout 10

title Debian Lenny
root (hd2,1)
kernel /boot/vmlinuz-2.6.18-6-486 root=UUID=fdf2f680-3dfe-40a2-b726-cd9b2ce86c85
initrd /boot/initrd.img-2.6.18-6-486

title Debian Lenny
root (hd2,1)
kernel /boot/vmlinuz-2.6.18-6-486 root=UUID=fdf2f680-3dfe-40a2-b726-cd9b2ce86c85
initrd /boot/initrd.img-2.6.18-6-486

=========================== sdi2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/update-grub using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
set default=0
set timeout=5
set root=(hd1,1)
if font (hd1,1)/usr/share/grub/unicode.pff ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  terminal gfxterm
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_hurd ###
### END /etc/grub.d/10_hurd ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, linux 2.6.27-7-generic" {
    linux    (hd1,1)/boot/vmlinuz-2.6.27-7-generic root=UUID=4eafc17c-1a55-45b9-be42-c26398ba0d7b ro quiet splash 
    initrd    (hd1,1)/boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu, linux 2.6.27-7-generic (single-user mode)" {
    linux    (hd1,1)/boot/vmlinuz-2.6.27-7-generic root=UUID=4eafc17c-1a55-45b9-be42-c26398ba0d7b ro single
    initrd    (hd1,1)/boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu, linux 2.6.27-11-generic" {
    linux    (hd1,1)/boot/vmlinuz-2.6.27-11-generic root=UUID=4eafc17c-1a55-45b9-be42-c26398ba0d7b ro quiet splash 
    initrd    (hd1,1)/boot/initrd.img-2.6.27-11-generic
}
menuentry "Ubuntu, linux 2.6.27-11-generic (single-user mode)" {
    linux    (hd1,1)/boot/vmlinuz-2.6.27-11-generic root=UUID=4eafc17c-1a55-45b9-be42-c26398ba0d7b ro single
    initrd    (hd1,1)/boot/initrd.img-2.6.27-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux    (hd1,1)/boot/memtest86+.bin
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista/Longhorn (loader) (on /dev/sda2)" {
    set root=(hd0,2)
    chainloader +1
}
menuentry "Ubuntu 8.10 (8.10) (on /dev/sda3)" {
    set root=(hd0,3)
    linux /boot/vmlinuz-2.6.27-11-generic root=/dev/sda3
    initrd /boot/initrd.img-2.6.27-11-generic
}
menuentry "Ubuntu 8.10 (8.10) (on /dev/sda3)" {
    set root=(hd0,3)
    linux /boot/vmlinuz-2.6.27-7-generic root=/dev/sda3
    initrd /boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu 8.10 (8.10) (on /dev/sda3)" {
    set root=(hd0,3)
    linux /boot/vmlinuz-2.6.27-9-generic root=/dev/sda3
    initrd /boot/initrd.img-2.6.27-9-generic
}
### END /etc/grub.d/30_os-prober ###

=============================== sdi2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sde2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdi        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sde1       /media/usb0     auto    rw,user,noauto  0       0
/dev/sde2       /media/usb1     auto    rw,user,noauto  0       0

=================== sdi2: Location of files loaded by Grub: ===================


   8.7GB: boot/grub/grub.cfg
   8.7GB: boot/grub/menu.lst
   8.7GB: boot/grub/stage2
   5.6GB: boot/initrd.img-2.6.18-6-486
   5.6GB: boot/vmlinuz-2.6.18-6-486
   5.6GB: initrd.img
   5.6GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf sdg sdh 

```

---

### Post by dragos240 on 2009-04-20
reply please? Can someone make sense of this output?

---

### Post by dragos240 on 2009-04-21
Bump

---

### Post by dragos240 on 2009-04-21
Nevermind. I solved it myself.

---


---
title: "booting Vista from GRUB: 'GRUB hard disk error'?"
date: 2009-05-11
forum: General Help
---

### Post by dajhull on 2009-05-11
Hi, I wonder if anyone can offer some advice on this. I'm running Ubuntu 8.10 and Windows Vista. I can mount the Vista partition from Ubuntu just fine, but when I try and boot Vista, GRUB just gives me a 'Hard Disk Error'. I'm guessing this means that there's a problem with my 'menu.lst', but I've tried all suggestions I can see on the forums and had no joy yet.

The following is the output from boot_info_script, if it's any use. 'menu.lst' and the output from 'fdisk -l' are in there, (plus other stuff that I don't understand but might be useful). Apparently the Vista partition is the boot partition. Is that correct? Any thoughts on this would be really appreciated.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda2 and 
                       looks at sector 1 on boot drive #119 for the stage2 
                       file. A stage2 file is at this location on /dev/sda. 
                       Stage2 looks on the same partition for 
                       /boot/grub/stage2. No errors found in the Boot 
                       Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x08f3c280

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048    94,538,891    91,464,844   7 HPFS/NTFS
/dev/sda3          94,542,525   312,576,704   218,034,180   5 Extended
/dev/sda5          94,542,588   311,339,699   216,797,112  83 Linux
/dev/sda6         311,339,763   312,576,704     1,236,942  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="F830007F300046DA" LABEL="WinRE" TYPE="ntfs" 
/dev/sda2: UUID="80C2F69090FA0800" LABEL="Vista" TYPE="ntfs" 
/dev/sda5: UUID="08363a3d-1325-4850-ba0c-629131aa9d24" TYPE="ext3" 
/dev/sda6: UUID="44001697-fe2e-4c5b-84ff-9cce88e57aa7" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/david/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=david)
/dev/sda1 on /media/WinRE type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /media/Vista type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sda5/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=08363a3d-1325-4850-ba0c-629131aa9d24 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=08363a3d-1325-4850-ba0c-629131aa9d24

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

title        Ubuntu 8.10, kernel 2.6.27-11-generic
uuid        08363a3d-1325-4850-ba0c-629131aa9d24
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=08363a3d-1325-4850-ba0c-629131aa9d24 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid        08363a3d-1325-4850-ba0c-629131aa9d24
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=08363a3d-1325-4850-ba0c-629131aa9d24 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        08363a3d-1325-4850-ba0c-629131aa9d24
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=08363a3d-1325-4850-ba0c-629131aa9d24 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        08363a3d-1325-4850-ba0c-629131aa9d24
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=08363a3d-1325-4850-ba0c-629131aa9d24 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        08363a3d-1325-4850-ba0c-629131aa9d24
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title        Windows Vista
root        (hd0,1)
makeactive
chainloader    +1

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=08363a3d-1325-4850-ba0c-629131aa9d24 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=44001697-fe2e-4c5b-84ff-9cce88e57aa7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  92.8GB: boot/grub/menu.lst
  92.9GB: boot/grub/stage2
  92.9GB: boot/initrd.img-2.6.27-11-generic
  92.8GB: boot/initrd.img-2.6.27-7-generic
  92.8GB: boot/vmlinuz-2.6.27-11-generic
  92.8GB: boot/vmlinuz-2.6.27-7-generic
  92.9GB: initrd.img
  92.8GB: initrd.img.old
  92.8GB: vmlinuz
  92.8GB: vmlinuz.old
```

---

### Post by cholericfun on 2009-05-11
have you just installed all this or were you previously able to boot into both OSs?

---

### Post by cholericfun on 2009-05-11
looking through you info i dont see anything wrong with anything...

just to be sure: 
did you try accessing files from Ubuntu and copying files across the partitions?


whats new to me though is the "hidden NTFS" partition.
whats that about - maybe thats irritating grub?

on the other hand you might want to try replacing root  = hda(0,1)
with
 UUID =...
in your menu.lst file

---

### Post by dajhull on 2009-05-11
Yeah I had 8.10 and Vista booting fine a while back, then I installed 9.04, and I think I must have told it to put GRUB on the Windows partition or something (does that makes sense, I'm not sure..), and since then Vista won't boot. I tried re-installing 8.10, which works again fine, but it didn't fix the Vista problem. It's no biggie, just that my university's wireless network doesn't seem to like Ubuntu. 

I think the hidden NTFS partition in a sort of windows recovery partition. (I think it's so Toshiba can cut costs by not shipping laptops with Windows DVDs). Ubuntu can mount that one too though, so I don't know what's hidden about it.

I tried the uuid hd(0,1)  but it gives me a Error 15.

Thanks for your help though, I actually learned quite a lot this morning, just fiddling about with this, so it ain't all bad!

---

### Post by cholericfun on 2009-05-11
well, maybe go ask the IT services at college what the deal is with the wireless..

other than that - maybe go through the motions of reinstalling the windows MBR (somehow.. not sure without the recovery disc) and then go with the LiveCD and set up grub again.

not sure if its of any help here but i find supergrubdisk is a great tool (in the repos)

PS - 
no i didnt mean UUID =hd(x,y)
UUID is some illegible number - i think its in your output for fdisk -l

```
/dev/sda2: UUID="80C2F69090FA0800" LABEL="Vista" TYPE="ntfs" 
```


this is just a wild guess though

---

### Post by Irishe on 2009-05-15
i'm no expert but i do have an idea.
I works for me in most instances where i multi-boot or Dual boot.

If you know how to access the Hidden Partition to restore your Vista
install then see if it has an option for a non-destructive restore,
If not then just restore vista to original and re-install ubuntu. 
It might not be the best way, but it may be an option.

i found to access one of my restore Partitions was to push f11 during 
the very beginning of Boot up. check with the Manufacture for your
particular system.

i also Noticed an Entry that doesn't seem right to me.

This Line seems to have more spaces then normal.
After bootmgr and after BCD.

/bootmgr /Boot/BCD /Windows/System32/winload.exe

 i doubt that it could be this simple but every observation is worth a try. 
i'd be curious to see how you fix this.
i been thinking of adding a distro of ubuntu to
My Multi-boot windows system.

---


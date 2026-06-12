---
title: "Can't boot Windows XP afte rinstalling Jaunty 9.04"
date: 2009-05-05
forum: General Help
---

### Post by photon_man62 on 2009-05-05
Hello. So my friend upgraded to Jaunty 9.04 from Intrepid 8.10, and he says he can't boot Windows XP anymore.

I got him to run the "bootinfo" script, here ya go:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader? is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 56. But according to the info from fdisk, 
                       sda5 starts at sector 440821304.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
28 heads, 56 sectors/track, 398687 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x194a7074

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             56   195,313,215   195,313,160  83 Linux
/dev/sda4         195,313,216   625,139,647   429,826,432   f W95 Ext d (LBA)
/dev/sda5         440,821,304   625,139,647   184,318,344   7 HPFS/NTFS
/dev/sda6         195,313,328   201,172,831     5,859,504  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 515 MB, 515768320 bytes
16 heads, 32 sectors/track, 1967 cylinders, total 1007360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe23be23b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     1,007,359     1,007,328   e W95 FAT16 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="66e96594-ba5b-456c-987f-0b734257f71b" TYPE="ext3" 
/dev/sda5: UUID="C644280A4427FC35" TYPE="ntfs" 
/dev/sda6: UUID="2c05b00b-2cc8-4810-9d78-8b80d53c99ef" TYPE="swap" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="ASAP" UUID="A28F-4754" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/lukasz/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=lukasz)
/dev/sdb1 on /media/ASAP type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sda5 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=66e96594-ba5b-456c-987f-0b734257f71b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=66e96594-ba5b-456c-987f-0b734257f71b

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
uuid		66e96594-ba5b-456c-987f-0b734257f71b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=66e96594-ba5b-456c-987f-0b734257f71b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		66e96594-ba5b-456c-987f-0b734257f71b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=66e96594-ba5b-456c-987f-0b734257f71b ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		66e96594-ba5b-456c-987f-0b734257f71b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=66e96594-ba5b-456c-987f-0b734257f71b /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2c05b00b-2cc8-4810-9d78-8b80d53c99ef none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  46.2GB: boot/grub/menu.lst
  46.2GB: boot/grub/stage2
  46.3GB: boot/initrd.img-2.6.28-11-generic
  46.2GB: boot/vmlinuz-2.6.28-11-generic
  46.3GB: initrd.img
  46.2GB: vmlinuz

```

I've noticed there is no entry for Windows XP in his menu.lst file, but I don't know what formula to use when adding it. Hope that's a lead.

---

### Post by zero7404 on 2009-05-05
i can't help with the error you're having, sorry. but i did find that clonezilla is excellent for backup/restore of partitions...

i have a dual boot system with vista x64 installed on the first NTFS partition, ubuntu is installed on the second ext3 partition, a swap partition as 3rd....

i went to 9.04 and i did not like it, so i used clonezilla to restore a backup i created of 8.10. when backing up, it also saved grub, and upon restore it restored grub (you can choose at the time of restore whether to restore grub or not).

since then, i have been able to boot into both OS's without a problem....restore was transparent and seamless....

i guess something you may want to try as well is to insert your XP cd in the drive, let it go thru repair of windows, it will restore the MBR for windows only. But not sure of how to handle starting back up in ubuntu, i am sure there is a way....

---

### Post by danwood76 on 2009-05-05
It looks like you've shifted your XP into an extended partition.
I'm pretty sure it wont boot from there even if you have the correct grub command.

Did you upgrade from a live CD or was it through synaptic?

You could try adding this to your grub:
```

title Windows XP (hd0)
root (hd0,4)
makeactive
chainloader +1

```

---

### Post by photon_man62 on 2009-05-05
Hmm...

He added that, and XP appears in the menu, but he can't boot it. And he updated through the CD.

---

### Post by caljohnsmith on 2009-05-05
It looks like you have a few issues preventing you from booting Windows XP right now; as Danwood76 all ready pointed out, Windows XP is on a logical partition, and to boot XP directly from a logical partition actually takes special steps. For one thing, probably the biggest factor preventing you from booting XP right now is that the XP partition is missing all its boot files. Did you have an NTFS/FAT primary partition that you deleted when installing Ubuntu? If so, that's most likely where Windows' boot files were. The other issue is that you'll have to fix Windows XP boot sector before you will be able to boot it successfully, because the embedded information in the boot sector about the start of the partition is wrong. 

But the good news is there is an excellent tutorial written by forum member meierfra about [how to boot Windows from a logical partition using Grub]("http://ubuntuforums.org/showthread.php?t=813628"). I would suggest following that tutorial, and when you modify your boot.ini file as per the directions in that tutorial, you should use "partition(2)". Anyway, let me know how that goes or if you run into problems.

Cheers,
John

---

### Post by danwood76 on 2009-05-05
The reason why it cant boot is because the XP partition has been moved to an extended partition. Windows (all versions even the latest windows 7) doesnt like it if its not center of attention on a primary partition and partition 1 (its possible to boot off partitions other than 1 but it must be primary).

To recover your XP you will need to move the XP partition back to the start of the drive and be partition 1, you will probably end up borking your Ubuntu install in doing this but just make sure you have a backup.

This can be done from a live CD using gparted (I think its in the admin menu by default called partition editor). Basically you will want to delete the Ubuntu partition and move (or copy if it wont let you move) the XP partition to the start of the drive as partition 1.
Then I would restart and insert the XP install CD, go to the recovery console and run fixmbr and with a bit of luck XP will boot again.
Then  you can have a go at reinstalling Ubuntu being careful with its partition layout.

If you dont have much of a clue with moving partitions then you will probably have to re install XP, I dont get why it was moved in the first place though!

-- edit --

Looks like I was a little late, nice guide john never realised you could boot off a logical partition!

---

### Post by photon_man62 on 2009-05-05
Yup, he just told me he deleted his Vista partition, since he had XP, Vista AND Ubuntu. I bet that's where the boot files were.

---

### Post by photon_man62 on 2009-05-05
> **caljohnsmith said:**
> ...[b]let me know how that goes or if you run into problems[b]...

Which partition should I mount?

He has a few partitions that say NTFS or Win95...

---

### Post by caljohnsmith on 2009-05-05
> **photon_man62 said:**
> Which partition should I mount?

He has a few partitions that say NTFS or Win95...
I think you are getting confused by the sda4 extended partition, which is merely a container for the logical partitions; you can't actually mount an extended partition, you can only mount the logical partitions inside of it. So to answer your question, you would want to mount the sda5 logical partition, because that has your Windows XP. :)

John

---

### Post by photon_man62 on 2009-05-05
Nvm, it's /dev/sda5.

---

### Post by photon_man62 on 2009-05-05
OK, so now it says

```
Use

title XP
rootnoverify (hd0,4)
chainloader +1


Do NOT use "makeactive".
Of course (hd0,4) needs to be adjusted. The first number is the hard drive and the second number the partition. Grubs starts counting at zero, and counts the hard drives according to the order in the bios. So the boot drive is always (hd0). The second number is always one less than the number in the device name. So if Windows is /dev/sda5, then the second number is 4.
The "hd" is always "hd", even if the device name contains "sd".
If Windows is not on the boot drive, you need to add "map" lines:

title XP
rootnoverify (hd3,4)
map (hd0) (hd3)
map (hd3) (hd0)
chainloader +1
```

So what should **I** use in MY case?

---

### Post by caljohnsmith on 2009-05-05
Since Windows is in sda5 on the same drive as Ubuntu, you can use:
```
title XP
rootnoverify (hd0,4)
chainloader +1

```

---

### Post by photon_man62 on 2009-05-05
He decided to wipe his drive clean, since he just made a mess of his disk.

Now, I need to find a way to wipe the disk (DBaN is a good idea, but he's out of CDs, and he can't install it on a flash drive form Ubuntu).

---


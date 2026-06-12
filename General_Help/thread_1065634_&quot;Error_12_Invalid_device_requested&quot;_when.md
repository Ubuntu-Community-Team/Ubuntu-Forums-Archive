---
title: "&quot;Error 12: Invalid device requested&quot; when booting into Windows"
date: 2009-02-10
forum: General Help
---

### Post by carpeme on 2009-02-10
Looks like somebody had a similar issue yesterday, though I've been unable to solve mine, so here goes.

Windows was working fine, but I installed Linux then accidentally wrote over my grub config. Now I'm trying to reconfigure grub to boot into Windows, without any success.

[This thread]("http://ubuntuforums.org/showpost.php?p=6701455&postcount=3") mentioned using a [boot info script]("https://sourceforge.net/projects/bootinfoscript/") for diagnostic purposes: below is the output of that script.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   /wubildr.mbr

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x333c333c

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,065   312,576,704   312,560,640   f W95 Ext d (LBA)
/dev/sda5    *         16,128   159,461,189   159,445,062   7 HPFS/NTFS
/dev/sda6         310,616,838   312,576,704     1,959,867  82 Linux swap / Solaris
/dev/sda7         263,739,168   310,616,774    46,877,607  83 Linux
/dev/sda8         159,461,253   263,739,104   104,277,852  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda5: UUID="284038244037F762" TYPE="ntfs" 
/dev/sda6: UUID="56eafe80-8580-4a6e-9035-0bec9c14330b" TYPE="swap" 
/dev/sda7: UUID="beb8ad2b-3f75-4651-a268-28c5835fb88d" TYPE="ext3" 
/dev/sda8: LABEL="store" UUID="0165370c-04ad-4fc2-bf97-82103733e52f" TYPE="ext2" 

=============================== "mount" output: ===============================

/dev/sda7 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/carpeliam/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=carpeliam)

=========================== sda7/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saied' instead of a number. In this case, the default entry
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

title Windows XP
rootnoverify (hd0,4)
#map (hd0,0) (hd0,4)
#map (hd0,4) (hd0,0)
savedefault
makeactive
chainloader +1

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
# kopt=root=UUID=beb8ad2b-3f75-4651-a268-28c5835fb88d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=beb8ad2b-3f75-4651-a268-28c5835fb88d

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		beb8ad2b-3f75-4651-a268-28c5835fb88d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=beb8ad2b-3f75-4651-a268-28c5835fb88d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		beb8ad2b-3f75-4651-a268-28c5835fb88d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=beb8ad2b-3f75-4651-a268-28c5835fb88d ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		beb8ad2b-3f75-4651-a268-28c5835fb88d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=beb8ad2b-3f75-4651-a268-28c5835fb88d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		beb8ad2b-3f75-4651-a268-28c5835fb88d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=beb8ad2b-3f75-4651-a268-28c5835fb88d ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		beb8ad2b-3f75-4651-a268-28c5835fb88d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=beb8ad2b-3f75-4651-a268-28c5835fb88d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		beb8ad2b-3f75-4651-a268-28c5835fb88d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=beb8ad2b-3f75-4651-a268-28c5835fb88d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		beb8ad2b-3f75-4651-a268-28c5835fb88d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=beb8ad2b-3f75-4651-a268-28c5835fb88d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=56eafe80-8580-4a6e-9035-0bec9c14330b none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 142.0GB: boot/grub/menu.lst
 142.0GB: boot/grub/stage2
 146.7GB: boot/initrd.img-2.6.27-11-generic
 142.1GB: boot/initrd.img-2.6.27-7-generic
 142.4GB: boot/initrd.img-2.6.27-9-generic
 143.0GB: boot/vmlinuz-2.6.27-11-generic
 142.0GB: boot/vmlinuz-2.6.27-7-generic
 145.9GB: boot/vmlinuz-2.6.27-9-generic
 146.7GB: initrd.img
 142.4GB: initrd.img.old
 143.0GB: vmlinuz
 145.9GB: vmlinuz.old

```

I tried changing my Windows setup in menu.lst to this:

```
title Windows XP
root (hd0,4)
chainloader +1
```

and this gives me a "A Disk Read Error Occured. Press CTRL+ALT+DEL to restart" error message when I try to boot into Windows. Booting into Linux works fine regardless.

I don't see any hard drive issues on the disk. Also, using the Windows Recovery Console, I'm able to successfully authenticate as the Administrator user for my Windows installation, so I know that it's still intact. I can read files on the partition from either the Windows Recovery Console or from ubuntu, but running "fixmbr" or "fixboot" in the Recovery Console leaves me with a "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER" message.

I'm guessing I've got a problem with my MBR, so I'm looking for a solution that doesn't involve reformatting/installing Windows from scratch.

---

### Post by caljohnsmith on 2009-02-10
It looks like the issue is that you have Windows installed to a logical partition, sda5, and any time you install Windows to a logical partition, it will put its boot files in a primary NTFS/FAT partition. The problem is you don't have a primary NTFS/FAT partition (at least not any more), so Windows is missing its necessary boot files. To fix the problem, how about downloading the attached "WinXP_boot_files1.zip" to your Ubuntu desktop, and do:
```
sudo mount /dev/sda5 /mnt
cd ~/Desktop
unzip WinXP_boot_files1.zip
sudo mv boot.ini ntldr NTDETECT.COM /mnt
```
Also, please change your Windows XP entry in your Grub menu.lst to simply:
```
title Windows XP
rootnoverify (hd0,4)
chainloader +1
```
In other words, it is important not to use a "makeactive" line, because Grub can't set the boot flag on a logical partition, i.e. make it active. Then reboot and let me know how far you get when you choose Windows from your Grub menu. We can work from there if necessary.

---

### Post by carpeme on 2009-02-10
caljohnsmith, thanks for the reply- glad I finally have the grub config down.

For those files, quick q- I have 64-bit XP, not 32-bit. I was able to find the files NTDETECT.COM and ntldr in the i386 directory of my install CD. I'm sure the boot.ini is fine, but the other two are binary files- is there anything to be concerned with here?

---

### Post by caljohnsmith on 2009-02-10
> **carpeme said:**
> caljohnsmith, thanks for the reply- glad I finally have the grub config down.

For those files, quick q- I have 64-bit XP, not 32-bit. I was able to find the files NTDETECT.COM and ntldr in the i386 directory of my install CD. I'm sure the boot.ini is fine, but the other two are binary files- is there anything to be concerned with here?
That's a good question, and I bet you are right; I would use the ntldr and NTDETECT.COM from your 64-bit Windows Install CD in case it is an issue. I forgot you might be using 64-bit, although I'm not sure if there is a difference with those boot files between 64-bit and 32-bit Windows versions. But I'm sure you're right about the boot.ini file though not mattering, because that is merely a text flle. If you have the time, I would be really interested to know if you can boot with the ntldr and NTDETECT.COM files I provided, because it would help my understanding to know if there is a difference with those files between the 64-bit and 32-bit Windows versions. Anyway, let me know how it goes.

---

### Post by carpeme on 2009-02-10
I tried both the version in your attachment as well as the one on the XP64 install CD, and neither one worked- in both cases, I get a "A Disk Read Error Occured. Press CTRL+ALT+DEL to restart" message.

Curious thing is, the files are in the i386 directory of the CD, there aren't any corresponding files in the x64 directory. I'm not sure if that means anything.

---

### Post by carpeme on 2009-02-10
Another thing- I was googling how to fix grub (I had tried fixmbr from the Windows Recovery Console after adding those files, but it didn't work), and came upon this in a [forum post]("http://ubuntuforums.org/archive/index.php/t-24113.html"):

> If you are multi-booting with Windows, make sure you do NOT install the MBR on the active partition (say /dev/hda1) but on the drive (/dev/hda). At least with Windows XP, you will have to re-install it (FIXMBR/FIXBOOT won't work).

I'm not sure if that's pertinent? And, if so, I'm not sure how to install the MBR on the disk itself as opposed to the partition.

---

### Post by caljohnsmith on 2009-02-10
OK, sounds like your Windows boot sector probably needs to be repaired; that's often required when you install Windows to a logical partition and then try to boot Windows directly from the logical partition. So to see if that is necessary, first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "No log", choose the correct HDD and "Proceed", choose "Intel", choose "Advanced", select the Windows sda5 partition, choose "Boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". After you are done doing the "Rebuild BS" in testdisk, reboot and let me know exactly what happens when you boot Windows XP from the Grub menu. We can work from there.

---

### Post by carpeme on 2009-02-10
caljohnsmith: you are the man. If anybody ever tells you otherwise, refer them to me.

Windows boots just fine after running through testdisk.

To make ubuntu the default when booting up, do I just need to change "default 0" in menu.lst to "default 1"?

---

### Post by caljohnsmith on 2009-02-10
> **carpeme said:**
> 
To make ubuntu the default when booting up, do I just need to change "default 0" in menu.lst to "default 1"?
Really glad to hear that testdisk did the trick. About making Ubuntu the default OS, you have it exactly right. Cheers and enjoy Ubuntu and Windows. :)

---

### Post by iliveinthedark on 2009-04-03
I followed this entire instructional, except i dont have a "write" option when i am in testdisk. I have dump, list and quit.

---

### Post by meierfra. on 2009-04-03
> I followed this entire instructional, except i dont have a "write" option when i am in testdisk. I have dump, list and quit.

That's ok. It means that your XP boot sector does not need to be fixed.

Did you try booting into XP? Did  you get any error messages?

Could you also run the boot info script and post the RESULTS.txt:

Download the  [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/")  to  your desktop.
Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file on your  desktop; please copy/paste the contents of the RESULTS.txt file to your next post, (use the code tags)

---


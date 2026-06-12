---
title: "Grubs loads itself"
date: 2009-01-23
forum: General Help
---

### Post by Gortzilla on 2009-01-23
I recently installed Windows 7 Beta which of course messed up the MBR, which I thought I fixed. Grubs seems to start off fine. I get the most recent Ubuntu Kernel, memtest and Windows XP. When I choose XP, Grubs just starts over again. I can choose any of the others, and they work. I don't know why this is happening. Thanks for any help in advance.

---

### Post by caljohnsmith on 2009-01-23
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by Gortzilla on 2009-01-23
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 359608408 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: you must specify the filesystem type

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda5 and looks 
                       at sector 337440840 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x97d997d9

Partition  Boot        Start          End         Size  Id System

/dev/sda1    *            63  309,620,744  309,620,682   7 HPFS/NTFS
/dev/sda2        309,620,745  488,392,064  178,771,320   5 Extended
/dev/sda5        309,620,808  387,439,604   77,818,797  83 Linux
/dev/sda6        486,271,548  488,392,064    2,120,517  82 Linux swap / Solaris
/dev/sda7        387,439,668  486,271,484   98,831,817   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda5: UUID="2dc38d9a-42e7-4ee9-b385-3956efd268f7" TYPE="ext3" 
/dev/sda6: UUID="2380fd1a-3486-4568-98db-c585573a7c0b" TYPE="swap" 
/dev/sda7: UUID="02E3F86477312125" TYPE="ntfs" 

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
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/tim/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tim)

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		15

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=2dc38d9a-42e7-4ee9-b385-3956efd268f7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
# defoptions=quiet splash vga=769

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
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=2dc38d9a-42e7-4ee9-b385-3956efd268f7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=2dc38d9a-42e7-4ee9-b385-3956efd268f7 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

##title		Ubuntu 8.10, kernel 2.6.27-7-generic
##root		(hd0,4)
##kernel		/boot/vmlinuz-2.6.27-7-generic ##root=UUID=2dc38d9a-42e7-4ee9-b385-3956efd268f7 ro quiet splash 
##initrd		/boot/initrd.img-2.6.27-7-generic
##quiet

##title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
##root		(hd0,4)
##kernel		/boot/vmlinuz-2.6.27-7-generic ##root=UUID=2dc38d9a-42e7-4ee9-b385-3956efd268f7 ro  single
##initrd		/boot/initrd.img-2.6.27-7-generic

#title		Ubuntu 8.10, kernel 2.6.24-21-generic
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2dc38d9a-42e7-4ee9-#b385-3956efd268f7 ro quiet splash 
#initrd		/boot/initrd.img-2.6.24-21-generic
#quiet

#title		Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2dc38d9a-42e7-4ee9-#b385-3956efd268f7 ro  single
#initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1




=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=2dc38d9a-42e7-4ee9-b385-3956efd268f7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=8a9ff822-37de-4625-82a9-4d70557bf25d none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location  of files loaded by Grub: ===================


 180.9GB: boot/grub/menu.lst
 184.1GB: boot/grub/stage2
 172.8GB: boot/initrd.img-2.6.24-21-generic
 172.8GB: boot/initrd.img-2.6.24-21-generic.bak
 172.7GB: boot/initrd.img-2.6.27-7-generic
 172.8GB: boot/initrd.img-2.6.27-9-generic
 172.8GB: boot/vmlinuz-2.6.24-21-generic
 172.7GB: boot/vmlinuz-2.6.27-7-generic
 172.7GB: boot/vmlinuz-2.6.27-9-generic
 172.8GB: initrd.img
 172.7GB: initrd.img.old
 172.7GB: vmlinuz
 172.7GB: vmlinuz.old

=============================== StdErr Messages: ===============================

/dev/sda1: unknown volume type
```

I see a problem, sda1 should be XP.

---

### Post by caljohnsmith on 2009-01-24
Yes, you're right, it looks like sda1 should be your XP install, and yet at some point you accidentally installed Grub to the boot sector of that partition. For future reference, I would try to avoid doing "setup (hd0,0)" in the Grub command line, because that will install Grub to the boot sector of your XP partition like what happened. Fortunately that type of problem is usually easy to fix, just boot your Windows XP Install CD, go to the "recovery console" and do:
```
fixboot
```
Then reboot, and you should be able to boot straight into Windows if all goes well. Once you are sure that's working, I would recommend installing Grub to the MBR (Master Boot Record) so you can dual boot, which I assume is your goal. To do that, try the following from your Live CD:
```
sudo grub
grub> root (hd0,4)
grub> setup (hd0)
grub> quit

```
Then reboot, and I think you should be all set. Let me know how it goes or if you run into problems.

---

### Post by Gortzilla on 2009-01-24
Thanks for the help. I figured it was something like that. I've tried it but forgot my XP admin password :oops:. I have it written somewhere, and after finding it will report my results.

---

### Post by Gortzilla on 2009-01-24
I realized the partition Windows repair is showing is drive D. Under the Setup  choice of the XP CD, it shows drive D as having 50GB capacity (Which means it's Windows 7). If it is indeed Windows 7, why isn't XP showing up on the list, and will this still work? Thanks for the help so far.

---

### Post by caljohnsmith on 2009-01-24
XP isn't showing up in the list because it is neither mountable nor readable at this point, because installing Grub to its boot sector made it corrupt. Can you do:
```
fixboot C:
```
From the XP CD? Just make sure not to do it on your Windows 7 partition.

---

### Post by Gortzilla on 2009-01-24
Sorry for my ignorance, but when I start the Windows XP recovery, I'm asked to first choose an account to log on to, which I choose the only one. I'm then prompted for the administrator password. My Windows 7 password doesn't work, nor does my XP password. Is there a way to go through the recovery console without having to log onto an account?

---

### Post by caljohnsmith on 2009-01-24
> **Gortzilla said:**
> Sorry for my ignorance, but when I start the Windows XP recovery, I'm asked to first choose an account to log on to, which I choose the only one. I'm then prompted for the administrator password. My Windows 7 password doesn't work, nor does my XP password. Is there a way to go through the recovery console without having to log onto an account?
That's a good question, because if your XP password doesn't work, I'm not sure how to get around that off-hand. Let's try another approach; how about booting your Windows 7 Install CD, go to the command line and do:
```
diskpart
```
And at the diskpart prompt do:
```
list volume
exit
```
Find your XP partition drive letter (maybe "C"), and then do:
```
[COLOR="Blue"]E:[/COLOR]\boot\bootsect.exe /nt52 [COLOR="Blue"]C:
[/COLOR]
```
Replace "E" above with the drive letter of your Win 7 CD, and also replace "C" with the drive letter of the XP partition. I'm not sure if the Win 7 Install CD has the "bootsect" command available, but let me know and we can work from there.

---

### Post by Gortzilla on 2009-01-24
Here's what I get after entering the last command.```

x:\Sources>E:\boot\bootsect.exe /nt52 C:
Target volumkes will be updated with NTLDR compatible bootcode.

C: (\\?\Volume{1e22bcb8-ea4c-19dd-889e-806e6f6e6963})

Could not open the volume root directory:
The parameter is incorrect.

No bootcode was successfully updated.
```

---

### Post by Gortzilla on 2009-01-24
Good news! I tried the boot fix in Windows 7. I can now boot Windows 7 and XP. XP seems to be fine. I'll be more careful with the Grub menu this time. Thanks for all your help, you're amazing.

---

### Post by caljohnsmith on 2009-01-24
Glad to hear you fixed it using the Win 7 boot fix option; cheers and have fun with all your OSes. :)

---

### Post by cariboo on 2009-01-24
I'm not sure if COC allows this, but you can go [here]("http://home.eunet.no/pnordahl/ntpasswd/") for a utility that allows you to reset your forgotten XP administrators password.

Jim

---


---
title: "Went in over my head: Trouble booting into XP"
date: 2009-02-10
forum: General Help
---

### Post by jwbrase on 2009-02-10
I'm not quite sure where this belongs, so I'll put it under General Help.

Since about a week ago, I've had an Ubuntu 8.10 install dual booted with XP via Wubi. Everything was fine until I tried doing something that in retrospect appears to have been a bit over my head. I was a bit annoyed with the timeout on the bootloader menu, and I also wanted to have it default to Ubuntu instead of XP. So I tried installing and running Startup Manager. However, all that did was set up a GRUB bootloader that only ran if Ubuntu was selected in the Windows bootloader, and it didn't change the settings of the Windows bootloader. So now I had two layers of bootloader for Ubuntu, and hadn't managed to change what the first bootloader did. So then I went to the Wubi site to see what bootloader it used (I didn't yet know it was the Windows bootloader). The Wubi site also told me how to do what I wanted to do: I needed to go to control_panel > system > advanced > startup_and_recovery, and fiddle with timeout and default OS options there.

I did that, and it booted into Ubuntu fine, and for a few hours I thought everything was great. Then my brother wanted me to boot into XP so he could use the computer. So I restarted, and when the GRUB boot list came up, I selected the first Windows XP option (It gave me two, the text was identical for either, and I don't know what the difference is supposed to be). It pretty much immediately crashed and went back to GRUB. So I tried the second option, and it gave me the Windows bootloader, started to load when I selected XP, and then crashed and went back to the beginning of the boot cycle (a black screen, then the Dell splashscreen, then GRUB). I tried it again, and this time got an option to boot Windows into several flavors of safe mode. I tried all options given, and none of them would boot. So now I seem to be stuck in Ubuntu. I'm pretty sure that if I could get into XP I could just set the default OS under System>Advanced>Startup and Recovery back to XP, and everything would be fine. But of course, the very problem is that I can't get back into XP.

So how badly have I screwed things up?

---

### Post by caljohnsmith on 2009-02-10
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Windows booting problem might be.

---

### Post by jwbrase on 2009-02-10
> **caljohnsmith said:**
> In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it

Oftentimes I just type tags out myself. 

> . The results of that script will help clarify your setup and hopefully what the solution to your Windows booting problem might be.

The drive in question is the 250 GB one, sda. The 60 GB one, sdb, is the drive from another computer that suffered a motherboard failure last fall. It's in an external drive bay connected by USB. 

```
 ============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /boot.ini /ntldr 
                       /NTDETECT.COM /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa42d04a3

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       160,649       160,587  de Dell Utility
/dev/sda2    *        160,650   488,263,544   488,102,895   7 HPFS/NTFS


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders, total 120103200 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4b36bdea

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   120,085,874   120,085,812   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-0C16" TYPE="vfat" 
/dev/sda2: UUID="6CE254A8E2547872" TYPE="ntfs" 
/dev/loop0: UUID="25273830-3392-406a-99cf-dcee4616bcbb" TYPE="ext3" 
/dev/sdb1: UUID="1618BAF318BAD0CB" LABEL="Local Disk" TYPE="ntfs" 

=============================== "mount" output: ===============================

/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda2 on /host type fuseblk (rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/braseall/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=braseall)
/dev/sdb1 on /media/Local Disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

==================== sda2/ubuntu/disks/boot/grub/menu.lst: ====================

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
#timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
color white/black green/blue

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
# kopt=root=UUID=6CE254A8E2547872 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=6CE254A8E2547872 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=6CE254A8E2547872 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6CE254A8E2547872 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6CE254A8E2547872 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


======================== sda2/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

================================ sda2/boot.ini: ================================

[boot loader]

timeout=0

default=c:\wubildr.mbr

[operating systems]

c:\wubildr.mbr="Ubuntu"

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=================== sda2: Location of files loaded by Grub: ===================


   3.5GB: ubuntu/disks/boot/grub/menu.lst
  39.4GB: ubuntu/disks/boot/initrd.img-2.6.27-11-generic
  39.3GB: ubuntu/disks/boot/initrd.img-2.6.27-7-generic
   3.5GB: ubuntu/disks/boot/vmlinuz-2.6.27-11-generic
  12.7GB: ubuntu/disks/boot/vmlinuz-2.6.27-7-generic

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

c:\wubildr.mbr="Ubuntu"


```

---

### Post by caljohnsmith on 2009-02-10
OK, I think I see what is happening; your Windows boot.ini file is set to boot Grub4DOS (the Ubuntu Wubi boot manager) by default, and your Grub's menu.lst then has a an entry to boot Windows. Thus when you boot Windows from Grub, you just boot Grub4DOS again since that is the default right now in Windows boot.ini file. I think what I would do if I were in your shoes is change the default timeout in your boot.ini from 0 to say 3-5 seconds so you can choose to boot Windows or Ubuntu, but Ubuntu will still be the default if you don't do anything. Then if you want you could set the timeout in your menu.lst to 0 so you boot straight into Ubuntu when you boot Ubuntu from the Windows boot menu. If that sounds OK, how about first doing:
```
gksudo gedit /host/boot.ini
```
And change the timeout from 0 to say 3 or 5 seconds:
```
[boot loader]
[COLOR="Blue"]timeout=5[/COLOR]
default=c:\wubildr.mbr
[operating systems]
c:\wubildr.mbr="Ubuntu"
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```
Then to change your Ubuntu's menu.lst:
```
gksudo gedit /host/ubuntu/disks/boot/grub/menu.lst
```
Uncomment the timeout line and set it to 0 if you want:
```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
[COLOR="Blue"]timeout		0[/COLOR]
```
Then reboot, and let me know how it goes.

---

### Post by jwbrase on 2009-02-10
> **caljohnsmith said:**
> OK, I think I see what is happening; your Windows boot.ini file is set to boot Grub4DOS (the Ubuntu Wubi boot manager) by default, and your Grub's menu.lst then has a an entry to boot Windows. Thus when you boot Windows from Grub, you just boot Grub4DOS again since that is the default right now in Windows boot.ini file. I think what I would do if I were in your shoes is change the default timeout in your boot.ini from 0 to say 3-5 seconds so you can choose to boot Windows or Ubuntu, but Ubuntu will still be the default if you don't do anything. Then if you want you could set the timeout in your menu.lst to 0 so you boot straight into Ubuntu when you boot Ubuntu from the Windows boot menu. If that sounds OK, how about first doing:
```
gksudo gedit /host/boot.ini
```
And change the timeout from 0 to say 3 or 5 seconds:
```
[boot loader]
[COLOR="Blue"]timeout=5[/COLOR]
default=c:\wubildr.mbr
[operating systems]
c:\wubildr.mbr="Ubuntu"
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```


Yep, that was it. (Posting from XP now). I thought that unchecking the "Time to display list of operating systems" tickbox would remove the timeout, but instead it set it to time out after zero seconds. Is there any way to modify the boot.ini file so that the boot list will stay up until an OS is selected and never time out? Or do I just have to set it to an arbitrarily large number (I've currently got it set to 999 seconds).

---


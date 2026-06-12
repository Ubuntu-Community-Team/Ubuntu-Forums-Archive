---
title: "GRUB error 21, dual boot, two hard drives"
date: 2009-04-29
forum: General Help
---

### Post by didiercool on 2009-04-29
When I try to boot up I get:

> GRUB Loading stage1.5.

GRUB loading, please wait...
Error 21
And there it stops.

The computer is an old Dell Dimension 8200 desktop with two hard drives (40g and 30g).  I have windows xp on the 40g and am trying to install ubuntu 9.04 on the 30g.

I have tried employing the following procedures:
[http://ubuntuforums.org/showthread.php?t=62717](http://ubuntuforums.org/showthread.php?t=62717) (super grub, gets me into windows, still no luck with Ubuntu)

[http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html](http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html) (my BIOS has no such options)

[http://en.kioskea.net/forum/affich-25667-dual-boot-ubuntu-vista-grub-error-21](http://en.kioskea.net/forum/affich-25667-dual-boot-ubuntu-vista-grub-error-21) (doesn't seem to make any difference)

[http://www.linuxquestions.org/questions/linux-general-1/grub-error-21-338856/](http://www.linuxquestions.org/questions/linux-general-1/grub-error-21-338856/) (both hard drives are plugged securely in place)

I've also tried reinstalling Ubuntu using both 8.10 and 9.04.  Same set of problems with each.

Any other suggestions?  Is there a way to update the BIOS?  When I tell super grub to fix it I get this error:

> findf /boot/grub/menu.lst /grub/menu.lst /boot/grub/grub.conf /grub/grub.conf

Error 15: File not found

/grub/menu.lst and /grub/grub.conf really don't exist on either my Dell's installation of Ubuntu, but neither do they exist on my laptop's installation and it works just fine (it too is dual booting, though all from one hard drive, separate partitions).  The rest of those files do exist where they should exist and the /boot/grub/menu.lst looks fine from what I know of that file.

Any ideas?

---

### Post by zvacet on 2009-04-29
Here is [error 15]("http://users.bigpond.net.au/hermanzone/p15.htm#15") and [error 21.]("http://users.bigpond.net.au/hermanzone/p15.htm#21")

---

### Post by caljohnsmith on 2009-04-29
In order to get a clearer picture of your setup related to your booting problem, how about downloading the **Boot Info Script** to your Ubuntu Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and help us determine what the solution to your booting problem might be.

---

### Post by didiercool on 2009-04-29
Thank you so much for the help on this!!  Both to zvacet and caljohn.

Ok, here are the results of Boot Info Script:

```
============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe4651a0a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,156,224    78,156,162   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders, total 58633344 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000675f

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    57,175,334    57,175,272  83 Linux
/dev/sdb2          57,175,335    58,621,184     1,445,850   5 Extended
/dev/sdb5          57,175,398    58,621,184     1,445,787  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="AC3C691A3C68E0B6" TYPE="ntfs" 
/dev/sdb1: UUID="e849aff5-4aed-45c9-8a6b-24a544043f0d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="2662e172-b65a-497d-83d7-bf60788fe019" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 

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


================================ sda1/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


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
# kopt=root=UUID=e849aff5-4aed-45c9-8a6b-24a544043f0d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e849aff5-4aed-45c9-8a6b-24a544043f0d

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
uuid		e849aff5-4aed-45c9-8a6b-24a544043f0d
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e849aff5-4aed-45c9-8a6b-24a544043f0d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		e849aff5-4aed-45c9-8a6b-24a544043f0d
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e849aff5-4aed-45c9-8a6b-24a544043f0d ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		e849aff5-4aed-45c9-8a6b-24a544043f0d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=e849aff5-4aed-45c9-8a6b-24a544043f0d /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=2662e172-b65a-497d-83d7-bf60788fe019 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .2GB: boot/grub/menu.lst
    .3GB: boot/grub/stage2
    .3GB: boot/initrd.img-2.6.28-11-generic
    .2GB: boot/vmlinuz-2.6.28-11-generic
    .3GB: initrd.img
    .2GB: vmlinuz
```

Any ideas?
Thanks again for the help!!

---

### Post by caljohnsmith on 2009-04-29
It looks like you might have used the Super Grub Disk to install a Windows equivalent MBR (Master Boot Record) to your 40 GB Windows HDD, because neither of your HDDs have Grub installed to the MBR at this point. It would be easy to install Grub to the MBR of your 30 GB Ubuntu HDD, but the question is, can you go into your BIOS and change your boot order so the Ubuntu drive will boot first on start up? That would be the most ideal. If you can do that, you can install Grub to the MBR of your Ubuntu drive by doing:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```
And then you should at least be able to boot Ubuntu on start up. See if you can get that far, and if so, I can help you boot Windows from your Ubuntu Grub menu. Or let me know if you run into problems.

---

### Post by didiercool on 2009-04-29
Ok. in my BIOS I have the option of changing 'Primary Drive 1' from 'OFF' to 'auto' and it now reads 'Unknown Device.'  (I'm assuming that's my ubuntu hd)  However, in my Boot Sequence options I only have CD-ROM, Diskette Drive, and Hard-Disk Drive C:, there's no option for booting from different hd's.

After the change, I still just boot straight to XP.

I'm going to try the code you prescribed just in case, but I'm assuming it won't do anything since GRUB is really coming up anymore.

Any ideas?


K, what if I reinstalled windows to get rid of the Windows equivalent MBR and then ran the code you prescribed.  The only reason I always install windows first is because I've read that its difficult to get GRUB to talk to windows if you install Ubuntu before windows.  However, you are really smart and maybe you know how to make GRUB talk to windows in that situation... ?  Just a thought.
> if so, I can help you boot Windows from your Ubuntu Grub menu

---

### Post by CMJ Tech on 2009-04-29
I am new to linux and this may not be the solution that you are looking for, but I thought I would share.  I experienced the same error message trying to dual boot 2 linux OS.  I had ubuntu on my primary HD and was trying to install debian on my secondary HD.  Got the same Error 21 after debian install completed. After struggling with grub with no progress, I ended up re-partitioning my primary HD and installing debian on the same drive as my ubuntu.   
After reinstalling debian on the primary HD and rebooting the system, the new grub installed by debian pick up my ubuntu and debian installed on the primary drive and also the debian I had been trying to install on the secondary drive.
I know this solution is not perfect but it worked for me.

---

### Post by didiercool on 2009-04-29
That's usually what's worked for me!  I've installed XP/ubuntu on several single hd computers with no issues.  I just assume the problem I'm having is due to installing on seperate hd's (rather than just seperate partitions).  Part of it might also be my old BIOS.  I would upgrade it, but you need an old floppy disk to install it.

---

### Post by didiercool on 2009-04-29
Ok, I finally got the Ubuntu partition to boot, but I can only boot it if I use the screen where you choose where to go (ubuntu or XP) with the super grub cd.  I don't know what changed, because I didn't do anything differently.  Now, any ideas about how to make my computer boot correctly without the help of super grub?  So far no luck here.

Well, now that I can boot to both OS's I'm going to go ahead and move in to them, so if a fix requires re-installation, I'll just opt to boot from the cd every time.

---

### Post by caljohnsmith on 2009-04-29
Since your BIOS doesn't give you the option to change the boot order, I think your best bet is to try and boot Ubuntu from Windows. And that's actually great news you got Ubuntu to boot from the Super Grub Disk, because I was concerned about the Grub error 21 that you originally got; that error means "selected disc does not exist". That could mean that the Ubuntu drive is not even accessible on start up, but if you can use Super Grub to boot Ubuntu, the Ubuntu drive must be accessible. So to confirm how Grub "sees" the Ubuntu drive on start up, how about booting the Super Grub Disk again, and when you get the first main menu, press "c" to get the command line, and then enter the following:
```
grub> geometry (hd0)
```
That should show your Windows drive (i.e. only one partition llsted as type "7" which is the file system ID for NTFS). If that works, next try:
```
grub> geometry (hd1)
```
And that should show your Ubuntu drive (i.e. two partitions). Let me know if that works, and if so, I can give you directions for how to boot Ubuntu from Windows if you want.

---

### Post by didiercool on 2009-04-29
Hmm... I guess I'm not sure what was supposed to happen, but the first command gave me a couple lines of code.  It included a line that said it didn't recognise the filesystem I was pointing it to, but other than that, it looked fine to me.  The second command looked fine.  It did recognise the filesystem and acted like it did everything.  The end result didn't seem to change.  I still boot straight into windows unless I use super grub, then I can go into Ubuntu if I want.

Assuming that's what you expected to happen, I would love if you could show me how to boot Ubuntu from Windows!

Thanks again for all your help!!

---

### Post by caljohnsmith on 2009-04-29
OK, that's good news, it sounds like you can probably boot Ubuntu from Windows then. First install Grub to the MBR of your Ubuntu drive by doing the following from the Ubuntu Live CD:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```
Then to boot Ubuntu from Windows XP, I would recommend installing "Grub4DOS" into Windows; you can do that by downloading the [grub4dos 0.4.4 zip package]("http://download.gna.org/grub4dos/grub4dos-0.4.4-2008-07-21.zip") to Windows, unzip it, and then put the "grldr" file in your root C: directory. Next download the [grubinst 1.1]("http://download.gna.org/grubutil/grubinst-1.1-bin-w32-2008-01-01.zip") package, unzip it, and run the "grubinst_gui.exe" program to install Grub4DOS to the MBR of your Windows drive. And lastly, save the following as "menu.lst" in your root C: directory:
```
default 0
timeout 10

title Windows XP
root (hd0,0)
chainloader +1

title Ubuntu Grub Menu
rootnoverify (hd1)
chainloader +1
```
Then reboot, and let me know exactly what happens on start up. We can work from there. :)

John

---

### Post by didiercool on 2009-04-29
Ok, I did all of the above.  The Grub4Dos installer was hardly user friendly but I think I got it right.  There were two 'grldr' files.  One was an MBR file, the other just plain.  I put just the plain one in and tried to install Grub4Dos on it but nothing changed in the boot (still straight to windows).

When both grldr files were in the root directory, and I ran Grub4Dos on the MBR file, my boot failed entirely.  I got the following message recursively (blinking)

```
Try (hd0,0): NTFS5:
```

I would guess that I'm just doing the wrong thing with the Grub4Disk Installer...

For the first space, 'Disk', I marked my windows partition.

For the second, 'File', I denoted the grldr file (one, then the other)

The rest of the various options I left unchecked.  Is that what I'm supposed to do?  Any suggestions with that?

Thanks!

---

### Post by didiercool on 2009-04-30
SOLVED!!!

Ok, after my previous post, I ran super grub again and 'fixed' the linux partition once more.  After that final fix, the computer now boots independently into both ubuntu and windows!!

caljohnsmith, you are among my heroes!!  Thanks so much for guiding me through that and being patient!!

~peace

---

### Post by caljohnsmith on 2009-04-30
I'm really glad to hear you can now boot into Windows or Ubuntu, and I agree, the Grub4dos GUI could use some work as far as being more user friendly. As long as you can boot either of your OSes, that's the main thing though at this point. Cheers and enjoy your new Ubuntu install. :)

John

---


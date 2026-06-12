---
title: "Adding Windows to Grub - ERROR 12"
date: 2009-01-25
forum: General Help
---

### Post by whazzzzzup17 on 2009-01-25
Okay I been reading around and I can't find my error. I have like 5 operating systems on my computer, however I can't get my windows xp/vista/7, onto the bootmenu. It shows up on the bootmenu, however when I click it, it will say "Error 12"

Any help I would greatly appreciate it.

---

### Post by caljohnsmith on 2009-01-25
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by whazzzzzup17 on 2009-01-25
I actually fixed error 12, however now when I click to load an Operating system for windows, its says:
> Windows Failed to start. A recent hardware or software change might be the cause
File: \boot\BCD
Status: 0xc0000001

I'm thinking of just redoing my whole entire system, because I added way to many operating systems. This was my first time multibooting, so I added a lot of operating systems, so I can gain more knowledge out of it. 

Here are my results. Its a pretty big file.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #10 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #133130718 on boot drive #1
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /grldr /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Boot file info:     
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Boot file info:     
    Operating System:  Windows XP
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Boot file info:     
    Operating System:  Windows XP
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Boot file info:     
    Operating System:  Windows XP
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Boot file info:     
    Operating System:  Windows Vista
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda11: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1573ae08

Partition  Boot        Start          End         Size  Id System

/dev/sda1    *            63   20,482,874   20,482,812   7 HPFS/NTFS
/dev/sda2         20,482,875  160,071,659  139,588,785   f W95 Ext'd (LBA)
/dev/sda5         20,482,938   40,965,749   20,482,812   7 HPFS/NTFS
/dev/sda6         40,965,813   61,448,624   20,482,812   7 HPFS/NTFS
/dev/sda7         61,448,688   81,931,499   20,482,812   7 HPFS/NTFS
/dev/sda8         81,931,563  102,414,374   20,482,812   7 HPFS/NTFS
/dev/sda9        102,414,438  133,130,654   30,716,217   7 HPFS/NTFS
/dev/sda10       133,130,718  158,111,729   24,981,012  83 Linux
/dev/sda11       158,111,793  160,071,659    1,959,867  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd17e7469

Partition  Boot        Start          End         Size  Id System

/dev/sdb1                 63  586,067,264  586,067,202   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="66EC1C51EC1C1E3D" LABEL="Microsoft Classic Xp" TYPE="ntfs" 
/dev/sda5: UUID="02A8E31FA8E30FC9" LABEL="Microsoft Home Xp" TYPE="ntfs" 
/dev/sda6: UUID="2CE4B09DE4B06B2A" LABEL="Microsoft Performance Tweaks" TYPE="ntfs" 
/dev/sda7: UUID="6AB0756CB075401D" LABEL="Microsoft Xp Professional 1" TYPE="ntfs" 
/dev/sda8: UUID="C26421B86421B059" LABEL="Microsoft Xp Proffesional 2" TYPE="ntfs" 
/dev/sda9: UUID="36D025F3D025BA4F" LABEL="Microsoft  Vista" TYPE="ntfs" 
/dev/sda10: UUID="da7ddebe-fec9-4d2a-b15e-1e73f699d068" TYPE="ext3" 
/dev/sda11: UUID="c8d6d0d0-c008-4877-91fb-fbcfcd5e6239" TYPE="swap" 
/dev/sdb1: UUID="3CD04A72D04A3286" LABEL="Microsoft Storage" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda10 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/stephen/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=stephen)

================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(5)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(5)\WINDOWS="Microsoft Professional XP 2" /NOEXECUTE=OPTIN /FASTDETECT

multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Professonial XP 1" /NOEXECUTE=OPTIN /FASTDETECT

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Performance Tweaks XP" /FASTDETECT /NOEXECUTE=OPTIN

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Classic XP" /NOEXECUTE=OPTIN /FASTDETECT

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Home XP" /NOEXECUTE=OPTIN /FASTDETECT


========================== sda10/boot/grub/menu.lst: ==========================

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
# kopt=root=UUID=da7ddebe-fec9-4d2a-b15e-1e73f699d068 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=da7ddebe-fec9-4d2a-b15e-1e73f699d068

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		da7ddebe-fec9-4d2a-b15e-1e73f699d068
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=da7ddebe-fec9-4d2a-b15e-1e73f699d068 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		da7ddebe-fec9-4d2a-b15e-1e73f699d068
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=da7ddebe-fec9-4d2a-b15e-1e73f699d068 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		da7ddebe-fec9-4d2a-b15e-1e73f699d068
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=da7ddebe-fec9-4d2a-b15e-1e73f699d068 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		da7ddebe-fec9-4d2a-b15e-1e73f699d068
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=da7ddebe-fec9-4d2a-b15e-1e73f699d068 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		da7ddebe-fec9-4d2a-b15e-1e73f699d068
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

title	   Windows XP 2
root       (hd0,6)
map        (hd0) (hd6)
map        (hd6) (hd0)
chainloader +1

title	   Windows XP3
root       (hd0,5)
map        (hd0) (hd5)
map        (hd5) (hd0)
chainloader +1

title	   Windows XP4
root       (hd1,5)
map        (hd1) (hd5)
map        (hd5) (hd1)
chainloader +1

title	   Windows XP5
root       (hd2,5)
map        (hd5) (hd2)
map        (hd2) (hd5)
chainloader +1





=============================== sda10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda10
UUID=da7ddebe-fec9-4d2a-b15e-1e73f699d068 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda11
UUID=c8d6d0d0-c008-4877-91fb-fbcfcd5e6239 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================== sda10: Location  of files loaded by Grub: ==================


  78.9GB: boot/grub/menu.lst
  79.0GB: boot/grub/stage2
  78.9GB: boot/initrd.img-2.6.27-7-generic
  78.9GB: boot/initrd.img-2.6.27-9-generic
  78.9GB: boot/vmlinuz-2.6.27-7-generic
  78.9GB: boot/vmlinuz-2.6.27-9-generic
  78.9GB: initrd.img
  78.9GB: initrd.img.old
  78.9GB: vmlinuz
  78.9GB: vmlinuz.old

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-25
It looks like since you installed multiple versions of Windows to logical partitions, they all put their boot files in primary partition sda1. That means you'll need to boot all of your Windows installations using the Windows boot loader in sda1 it looks like, unless you want to go through a lot of trouble to move their boot files back to their respective partitions and reconfigure their boot files. What happens when you choose the "Windows Vista/Longhorn (loader)" first Windows entry in your Grub menu? Do you get a choice to boot the other Windows installations? If so, what happens?

---

### Post by whazzzzzup17 on 2009-01-25
When I chose "Windows Vista/Longhorn (loader)" on the grub menu, I get another menu that will say:
> Earlier Edition of Windows
Windows Vista Ultimate

If I click "Earlier Edition of Windows" it brings me to another menu that says the rest of my operating systems.

How would I fix this to make it in one menu? I plan on redoing my system any ways, so if I have to that completely start over, than I wouldn't mind it that much. I would just have back up all my data again. I eventually plan on just adding my Windows XP, Windows Vista, Windows 7, and Ubuntu 8.10. All this other crap I got on here is garbage anyways.

---

### Post by caljohnsmith on 2009-01-25
Well, if you want to go through the trouble of restoring the boot files to each Windows partition and reconfiguring the boot files, you wouldn't have to reinstall. If you want to try that, here is a really [good tutorial]("http://ubuntuforums.org/showthread.php?t=813628") of how to go about it. Keep in mind that Windows 7 is just like Vista as far as booting is concerned, so you can follow post #4 of that thread for both Vista and Win 7. Or if you decide to reinstall, I would recommend giving all your Windows installs their own primary partition, and also "hiding" the Windows partitions from each other when you install each Windows version; that should keep their boot files separate, and then you should be able to boot them all separately from Grub. Let me know if you want more info about how to do that.

---

### Post by whazzzzzup17 on 2009-01-25
How exactly do I make a partition "primary"? This was my first successful multiboot, and I was taught to just make them "Logical". Also how would I make the partition hidden from each other?

I also have another question, which is a little off topic, but since were on multibooting. Since this is my first time multibooting, I have made an extra partition to store "Data". For example I'll install "Mozilla Firefox" on one operating system and I will install it into a dictionary on my "Data" partition. However, if I load up a different operating system on start up, my profiles/information will be missing and will only be accessible if I load up the operating system in which I installed it from. 

> **Note:** When I mean "not accessible" I mean that some of the settings i had on the previous operating system are gone" I can still load firefox by navigating to my "Data" partition, its just that all the settings are back to default.

I did find away around this, and it was to navigate to "documents and settings> application data" and simply just coping the application folder to each of my operating systems.

Is there a better way of doing this? Would you suggest a different way on storing data between different operating systems?

Thanks

---

### Post by caljohnsmith on 2009-01-25
> **whazzzzzup17 said:**
> How exactly do I make a partition "primary"? This was my first successful multiboot, and I was taught to just make them "Logical". Also how would I make the partition hidden from each other?

You can have at most 4 primary partitions, or you can have 3 primary partitions and one extended partition, and inside the extended partition you can have as many logical partitions as you want. In linux, primary partitions are always numbered 1-4, like sda1-sda4, and the logical partitions always start at 5 and count from there, such as sda5, sda6, sda7, etc. You just have to specify to make the partition primary when you partition the drive with say gparted. To hide/unhide partitions, you can use Grub if you want:
```
sudo grub
grub> hide (hd0,0)   [COLOR="Blue"][hides sda1][/COLOR]
grub> hide (hd0,1)   [COLOR="Blue"][hides sda2][/COLOR]
grub> unhide (hd0,2) [COLOR="Blue"][unhides sda3][/COLOR]
...etc. 
```
So if you have XP installed on sda1 for example, when you go to install Vista on say sda2, you would want to first hide the sda1 partition so Vista won't be tempted to put its boot files in your XP partition. Once you are done installing Vista, you would unhide the XP partition. 
> **whazzzzzup17 said:**
> 
I also have another question, which is a little off topic, but since were on multibooting. Since this is my first time multibooting, I have made an extra partition to store "Data". For example I'll install "Mozilla Firefox" on one operating system and I will install it into a dictionary on my "Data" partition. However, if I load up a different operating system on start up, my profiles/information will be missing and will only be accessible if I load up the operating system in which I installed it from. 

I did find away around this, and it was to navigate to "documents and settings> application data" and simply just coping the application folder to each of my operating systems.

Is there a better way of doing this? Would you suggest a different way on storing data between different operating systems?

Thanks
I'm not sure what the best way is to share settings between all your Windows versions. You might want to ask that in a forum more geared towards Windows users. :)

---

### Post by whazzzzzup17 on 2009-01-25
Thank you for all your help. You defiantly have made me into an active member to this forum.

---


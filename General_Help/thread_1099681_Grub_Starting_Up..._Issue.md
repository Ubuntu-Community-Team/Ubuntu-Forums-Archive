---
title: "Grub Starting Up... Issue"
date: 2009-03-18
forum: General Help
---

### Post by GoVeganDummy on 2009-03-18
Hello, I am a brand new Linux user. I decided the other day to just jump in and I have encountered some boot/grub issues. I should say that I am dual booting Windows XP (32-bit) and Ubuntu 8.10 (64-bit). I have had various errors regarding the grub such as error 22, 17, 13, and now I am stuck on the starting up screen after I select to boot XP. bummer :( I would love to never use XP again, but I run audio programs that are Windows exclusive. 

Let me just say that I am running XP on my C:\ drive and Ubuntu on my E:\ drive. The E:\ drive only has linux on it right now, no other data whatsoever. 

At any rate, I have dealt with the other errors by reading the forum and getting some good help with code etc... However, like I said, I am BRAND NEW to linux and am becoming very frustrated with the grub crap, but I realize the issue here is probably XP. Can any one help? Do I need to give you any other specific info?

---

### Post by meierfra. on 2009-03-18
> now I am stuck on the starting up screen after I select to boot XP


Is this a black screen saying nothing but "starting up"?  

Could you post the output of

```
sudo fdisk -lu
```

and the Windows item you are currently using in "menu.lst"

(if the line makes not sense to you, post the output of "cat /boot/grub/menu.lst" instead)

---

### Post by GoVeganDummy on 2009-03-18
yes its a black screen that just says "Starting Up..." and is stuck there.

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1c26e063

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   293041664   146520801    7  HPFS/NTFS

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf3f861e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   288350684   144175311   83  Linux
/dev/sdb2       292961340   586099394   146569027+   5  Extended
/dev/sdb5       292961403   312496379     9767488+  82  Linux swap / Solaris
/dev/sdb6       312496443   574902089   131202823+  83  Linux
/dev/sdb7       574902153   586099394     5598621   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfa77c8b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   976784129   488392033+   7  HPFS/NTFS




# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows
rootnoverify (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

I know that Ubuntu is installed on the "b" drive and Windows is on the "a" drive, so hd1 is the b drive correct? my mind is boggled! thank you so much for your help.

---

### Post by meierfra. on 2009-03-18
The "starting up" is usually caused by missing "map" lines  in the Windows item on menu.lst or by a corrupt boot sector. Since  you are already  using the "map" lines, lets check on the boot sector of your windows partitions:

 Download the [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) to your desktop, and then do:

```


cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sda

```


Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose "boot"
"RebuildBS"
"Write"  

then press "q" a few times to quit  testdisk, reboot and see whether you can boot into Windows.
 (If it does not give you an option to "Write", it means that the original and rebuild boot sector are identical, and  testdisk RebuildBS won't be able to solve your problem)

---

### Post by GoVeganDummy on 2009-03-18
it does not give me an option to "write", only "dump", "list", or "quit". :(

---

### Post by meierfra. on 2009-03-18
It seems we have to dig deeper:

In order to get a clearer picture of your setup, I suggest to boot from your Ubuntu Live CD (the Ubuntu install CD), download the Boot Info Script to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by GoVeganDummy on 2009-03-18
ok give me a few minutes :)

---

### Post by meierfra. on 2009-03-18
Sorry, you don't need to boot from the LiveCD. Just do it from Ubuntu.

---

### Post by GoVeganDummy on 2009-03-18
hahaa ok let me go back.

---

### Post by GoVeganDummy on 2009-03-18
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

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
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc1 has 
                       976770080 sectors, but according to the info from 
                       fdisk, it has 976784067 sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1c26e063

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   293,041,664   293,041,602   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf3f861e4

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   288,350,684   288,350,622  83 Linux
/dev/sdb2         292,961,340   586,099,394   293,138,055   5 Extended
/dev/sdb5         292,961,403   312,496,379    19,534,977  82 Linux swap / Solaris
/dev/sdb6         312,496,443   574,902,089   262,405,647  83 Linux
/dev/sdb7         574,902,153   586,099,394    11,197,242  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfa77c8b2

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   976,784,129   976,784,067   7 HPFS/NTFS

/dev/sdc1 ends after the last sector of /dev/sdc

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="C088417988416ECA" TYPE="ntfs" 
/dev/sdb1: UUID="2b8d268c-26b1-433f-8b8c-6b57e2b6a159" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="43caa4a6-414b-4b47-8fa2-1c5b9aa9ddc6" TYPE="swap" 
/dev/sdb6: UUID="cc6ff6fd-6cc9-4157-be26-347f92c944bf" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb7: UUID="9cf389f1-72e6-4833-a51d-248d539d7ece" TYPE="swap" 
/dev/sdc1: UUID="A260CA7C60CA56A7" LABEL="DUDE" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd1 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

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
# kopt=root=UUID=2b8d268c-26b1-433f-8b8c-6b57e2b6a159 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2b8d268c-26b1-433f-8b8c-6b57e2b6a159

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		2b8d268c-26b1-433f-8b8c-6b57e2b6a159
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2b8d268c-26b1-433f-8b8c-6b57e2b6a159 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		2b8d268c-26b1-433f-8b8c-6b57e2b6a159
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2b8d268c-26b1-433f-8b8c-6b57e2b6a159 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		2b8d268c-26b1-433f-8b8c-6b57e2b6a159
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows
rootnoverify (hd1,5)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

================================ sdb1/menu.lst: ================================

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
# kopt=root=UUID=2b8d268c-26b1-433f-8b8c-6b57e2b6a159 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2b8d268c-26b1-433f-8b8c-6b57e2b6a159

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		2b8d268c-26b1-433f-8b8c-6b57e2b6a159
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2b8d268c-26b1-433f-8b8c-6b57e2b6a159 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		2b8d268c-26b1-433f-8b8c-6b57e2b6a159
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2b8d268c-26b1-433f-8b8c-6b57e2b6a159 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		2b8d268c-26b1-433f-8b8c-6b57e2b6a159
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
root		(hd1,0)
savedefault
makeactive
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=2b8d268c-26b1-433f-8b8c-6b57e2b6a159 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=43caa4a6-414b-4b47-8fa2-1c5b9aa9ddc6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


 102.3GB: boot/grub/menu.lst
 102.3GB: boot/grub/stage2
 102.4GB: boot/initrd.img-2.6.27-7-generic
 102.3GB: boot/vmlinuz-2.6.27-7-generic
 102.4GB: initrd.img
    .1GB: menu.lst
 102.3GB: vmlinuz

=========================== sdb6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=cc6ff6fd-6cc9-4157-be26-347f92c944bf ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=cc6ff6fd-6cc9-4157-be26-347f92c944bf

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		cc6ff6fd-6cc9-4157-be26-347f92c944bf
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cc6ff6fd-6cc9-4157-be26-347f92c944bf ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		cc6ff6fd-6cc9-4157-be26-347f92c944bf
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cc6ff6fd-6cc9-4157-be26-347f92c944bf ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		cc6ff6fd-6cc9-4157-be26-347f92c944bf
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
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2b8d268c-26b1-433f-8b8c-6b57e2b6a159 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2b8d268c-26b1-433f-8b8c-6b57e2b6a159 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, memtest86+ (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb6
UUID=cc6ff6fd-6cc9-4157-be26-347f92c944bf /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb7
UUID=9cf389f1-72e6-4833-a51d-248d539d7ece none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


 171.2GB: boot/grub/menu.lst
 171.2GB: boot/grub/stage2
 171.2GB: boot/initrd.img-2.6.27-7-generic
 171.1GB: boot/vmlinuz-2.6.27-7-generic
 171.2GB: initrd.img
 171.1GB: vmlinuz
```

---

### Post by meierfra. on 2009-03-18
Pretty confusing, you have  two different Ubuntu installs (sbd1 and sdb6) and three different "menu.lst"  
Also grub is correctly install to the MBR of sda and sdb.
So you could be booting from sda  (your Windows drive) or from sdb (the windows drive). Do you know which drive is first in the boot order?

The menu.lst you are using seems to be the /boot/grub/menu.lst on /dev/sdb1.  

So boot to your Ubuntu on /dev/sdb1 (which should be the only Ubuntu on your Grub menu) 

and  open "menu.lst" via

```
gksudo gedit /boot/grub/menu.lst
```

Add this five  items

title XP (hd0)
rootnoverify (hd0,0)
chainloader +1

title XP (hd1) map
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


title XP (hd1) no map
rootnoverify (hd1,0)
chainloader +1


title XP (hd2) map
rootnoverify (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

title XP (hd2) no map
rootnoverify (hd2,0)
chainloader +1



Reboot and try all these entries at the Grub menu.
You probably already tried most of these but just to make sure, try all of them again.

If one of them works, you can remove the remaining one from menu.lst

If none of them works, report all error messages you got. 
In this case,  I also recommend a file system check:


Boot from your XP CD and press "r" to get to the Windows repair console.
Type

```
chkdsk /r
```

If "chkdsk" fixed some errors, run it again until it does not find any more errors

---

### Post by GoVeganDummy on 2009-03-18
Ok will do. I realize that I have two installations because I tried to re-install Ubuntu in order to fix the grub issue. That may have been a bad idea :) How would I get rid of the second install?

I am going to try and boot now. thanks!

---

### Post by GoVeganDummy on 2009-03-18
OHH YEA!!!! I am in windows right now!!!  Thank you sooo much. I would still like to make the hard drive that has Ubuntu on it partitioned so that I can use a percentage of it for media storage in both Ubuntu and Windows. Any suggestions?

---

### Post by meierfra. on 2009-03-18
> OHH YEA!!!! I am in windows right now!!!

Which entry was the correct one?

> partitioned so that I can use a percentage of it for media storage in both Ubuntu and Windows.


Install  and run gparted (The Partition Editor) via

```
sudo apt-get install gparted
gksudo gparted &
```

Select /dev/sdb in the drop down box in the upper right.
Delete the last two partitions (/dev/sdb6 and /dev/sdb7)  (select  partition, right click and choose delete) 
Create a new partition  (right click the unallocated space, choose "new")  and format it as "ntfs".
Close gparted.


Cretate a directory for mounting your new storage partition:

```
sudo mkdir /media/Storage
sudo chown your_user_name:your_username /media/Storage
```


Open "fstab" via


```
gksudo gedit /etc/fstab
```

Add this line to the end

/dev/sdb6   /media/Storage ntfs-3g defaults,locale=en_US.UTF-8 0 0

and save the file.

Mount your new storage partition via

```
sudo mount -a
```
 and you should now  have an icon for your new Storage partition on the desktop. (Sometimes you have to reboot before it becomes effective)

---

### Post by GoVeganDummy on 2009-03-18
thank you sooooo much. 

```
title XP (hd2) map
rootnoverify (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1
```

was the winner. I have everything setup up just right now! thank you very very much.

---

### Post by meierfra. on 2009-03-18
> I have everything setup up just right now

Glad it all worked out.
Have fun with XP and Ubuntu.

---


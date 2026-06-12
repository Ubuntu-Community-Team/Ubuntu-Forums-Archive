---
title: "BOOTMGR MISSING on Windows XP dual-boot"
date: 2009-02-13
forum: General Help
---

### Post by zimbico on 2009-02-13
Hiya,

I'm new to all of this (I didn't really know where to post) and have installed ubuntu as a dual-boot on my computer along with the previously installed windows xp pro (on the same hdd).

Now, when I select Windows XP Professional from Grub, it says:
"BOOTMGR is missing.
Press Ctrl+Alt+Del to restart":confused:

I've moved to a new school and the amount of homework is incredible. I'd really counted on being able to play cod5 on xp in the only hour i've had spare in over a week, but instead spent the whole time trying unsuccessfully to get the stupid thing to boot.

It still starts ubuntu correctly at least.

How can I fix this?

Thanks, Brendan.

---

### Post by caljohnsmith on 2009-02-13
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Windows booting problem might be.

---

### Post by zimbico on 2009-02-13
Hey caljohnsmith,
Thanks for replying! I copied the code you posted into the terminal but it couldn't find the file. I then realised that I had misread your post, so I downloaded the script and then the terminal completed the operation:)
Here's the output file's contents:
```

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfe72a019

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   156,296,384   156,296,322   7 HPFS/NTFS


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xac23ac23

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63 1,743,727,229 1,743,727,167   7 HPFS/NTFS
/dev/sdb2       1,743,727,230 1,953,520,064   209,792,835   5 Extended
/dev/sdb5       1,743,727,293 1,944,893,159   201,165,867  83 Linux
/dev/sdb6       1,944,893,223 1,953,520,064     8,626,842  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="1F1678C3455CCC21" TYPE="ntfs" 
/dev/sdb1: UUID="5A18DE1318DDEDCF" TYPE="ntfs" 
/dev/sdb5: UUID="ed4cd4bc-1cbf-4981-9b2c-f4bc6c9f1741" TYPE="ext3" 
/dev/sdb6: TYPE="swap" UUID="6f6c5033-56b6-4758-b75e-f60d8fa518d6" 

=============================== "mount" output: ===============================

/dev/sdb5 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/brendan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=brendan)

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sdb5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=ed4cd4bc-1cbf-4981-9b2c-f4bc6c9f1741 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ed4cd4bc-1cbf-4981-9b2c-f4bc6c9f1741

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
uuid		ed4cd4bc-1cbf-4981-9b2c-f4bc6c9f1741
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ed4cd4bc-1cbf-4981-9b2c-f4bc6c9f1741 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ed4cd4bc-1cbf-4981-9b2c-f4bc6c9f1741
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ed4cd4bc-1cbf-4981-9b2c-f4bc6c9f1741 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ed4cd4bc-1cbf-4981-9b2c-f4bc6c9f1741
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


================================ sdb5/menu.lst: ================================

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
# kopt=root=UUID=ed4cd4bc-1cbf-4981-9b2c-f4bc6c9f1741 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ed4cd4bc-1cbf-4981-9b2c-f4bc6c9f1741

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
uuid		ed4cd4bc-1cbf-4981-9b2c-f4bc6c9f1741
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ed4cd4bc-1cbf-4981-9b2c-f4bc6c9f1741 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ed4cd4bc-1cbf-4981-9b2c-f4bc6c9f1741
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ed4cd4bc-1cbf-4981-9b2c-f4bc6c9f1741 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ed4cd4bc-1cbf-4981-9b2c-f4bc6c9f1741
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdb5/etc/fstab: ===============================

proc            /proc           proc    defaults        0       0
UUID=ed4cd4bc-1cbf-4981-9b2c-f4bc6c9f1741 /               ext3    relatime,errors=remount-ro 0       1
UUID=6f6c5033-56b6-4758-b75e-f60d8fa518d6 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 951.0GB: boot/grub/menu.lst
 951.1GB: boot/grub/stage2
 951.1GB: boot/initrd.img-2.6.27-7-generic
 951.1GB: boot/vmlinuz-2.6.27-7-generic
 951.1GB: initrd.img
 892.8GB: menu.lst
 951.1GB: vmlinuz

```

---

### Post by caljohnsmith on 2009-02-13
OK, it looks like the problem is that Grub's menu.lst is configured to boot the wrong partition for Windows; how about opening your menu.lst first:
```
gksudo gedit /boot/grub/menu.lst
```
And change your Windows entry to:
```
title		Microsoft Windows XP Professional
root		(hd0,0)
chainloader	+1

```
Reboot, try Windows again, and let me know how far you get. We can work from there if necessary.

---

### Post by zimbico on 2009-02-13
YAY! IT WORKED!
Thank you sooo much, caljohnsmith!!
You're a genius!

---

### Post by caljohnsmith on 2009-02-13
You're welcome, glad it turned out to be a simple fix. Cheers and enjoy Ubuntu and Windows. :)

---

### Post by zimbico on 2009-02-14
Just one more thing,
How can I make it so that Windows boots by default?

---

### Post by caljohnsmith on 2009-02-14
Just move the Windows entry directly above these lines in your menu.lst:
```
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
```
That should be all it takes, but let me know if you run into problems.

---

### Post by apamix on 2009-04-28
Can someone help me with my boot :? ... when i'm tring to boot in windows i get 
BOOTMGR is missing :( 

[code]============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/hdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/hdd
 => Windows is installed in the MBR of /dev/sda

hdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux squeeze/sid
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

hdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

hdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

hdd1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe 
                       /WINDOWS/system32/winload.exe 
                       /WINDOWS/SYSTEM32/winload.exe 
                       /windows/system32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: hdb ___________________ _____________________________________________________

Disk /dev/hdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf6d3f6d3

Partition  Boot         Start           End          Size  Id System

/dev/hdb1    *             63   155,525,264   155,525,202  83 Linux
/dev/hdb2         155,525,265   160,826,714     5,301,450   5 Extended
/dev/hdb5         155,525,328   160,826,714     5,301,387  82 Linux swap / Solaris


Drive: hdd ___________________ _____________________________________________________

Disk /dev/hdd: 40.0 GB, 40027029504 bytes
16 heads, 63 sectors/track, 77557 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0a690a68

Partition  Boot         Start           End          Size  Id System

/dev/hdd1    *             63    78,177,455    78,177,393  83 Linux


Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80025280000 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156299375 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x008a008a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    33,399,134    33,399,072   7 HPFS/NTFS
/dev/sda2          33,399,135   156,296,384   122,897,250   f W95 Ext d (LBA)
/dev/sda5          33,399,198   156,296,384   122,897,187   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/hdb1: UUID="a2c45682-418a-4e1f-8491-852f9a5fa6e1" TYPE="ext3" 
/dev/hdb5: UUID="4079239e-f8bc-4f3f-899f-bab9ee1f561a" TYPE="swap" 
/dev/hdd1: TYPE="ext3" 
/dev/sda1: UUID="CED07536D07525BD" TYPE="ntfs" 
/dev/sda5: UUID="15185FD958B89881" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/hdd1 on /mnt/maxtor type ext3 (rw)
/dev/sda5 on /mnt/sata type fuseblk (rw,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)


=========================== hdb1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/hdb1 ro

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
# defoptions=quiet

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

title        Debian GNU/Linux, kernel 2.6.26.8
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.26.8 root=/dev/hdb1 ro quiet
initrd        /boot/initrd.img-2.6.26.8

title        Debian GNU/Linux, kernel 2.6.26.8 (single-user mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.26.8 root=/dev/hdb1 ro single
initrd        /boot/initrd.img-2.6.26.8

title        Debian GNU/Linux, kernel 2.6.26-1-686
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.26-1-686 root=/dev/hdb1 ro quiet
initrd        /boot/initrd.img-2.6.26-1-686

title        Debian GNU/Linux, kernel 2.6.26-1-686 (single-user mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.26-1-686 root=/dev/hdb1 ro single
initrd        /boot/initrd.img-2.6.26-1-686

### END DEBIAN AUTOMAGIC KERNELS LIST
splashimage=(hd0,0)/boot/grub/77942-wolf.xpm.gz

title Windows
map (hd0) (hd2)
map (hd2) (hd0)
rootnoverify (hd2,0)
chainloader +1
boot



=============================== hdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd1      /mnt/maxtor      ext3    defaults 0 0 
/dev/sda5      /mnt/sata        ntfs-3g    umask=0,nls=utf8 0 0

=================== hdb1: Location of files loaded by Grub: ===================


  22.4GB: boot/grub/menu.lst
  22.3GB: boot/grub/stage2
  22.4GB: boot/initrd.img-2.6.26-1-686
  22.3GB: boot/initrd.img-2.6.26-1-686.bak
  22.3GB: boot/initrd.img-2.6.26.8
  22.3GB: boot/vmlinuz-2.6.26-1-686
  22.3GB: boot/vmlinuz-2.6.26.8
  22.4GB: initrd.img
  22.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on hdd1

00000000  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 f6 f6 f6 f6  |................|
*
00000200

Unknown BootLoader  on sda2

00000000  37 06 44 06 48 06 28 06  29 06 20 00 48 06 2a 06  |7.D.H.(.). .H.*.|
00000010  39 06 2f 06 4a 06 44 06  47 06 27 06 0c 06 20 00  |9./.J.D.G.'... .|
00000020  39 06 46 06 2f 06 20 00  41 06 2a 06 2d 06 20 00  |9.F./. .A.*.-. .|
00000030  27 06 44 06 45 06 44 06  41 06 27 06 2a 06 20 00  |'.D.E.D.A.'.*. .|
00000040  27 06 44 06 45 06 48 06  33 06 39 06 29 06 2e 00  |'.D.E.H.3.9.)...|
00000050  0d 00 0a 00 0d 00 0a 00  27 06 44 06 27 06 41 06  |........'.D.'.A.|
00000060  2a 06 31 06 27 06 36 06  4a 06 3a 00 20 00 41 00  |*.1.'.6.J.:. .A.|
00000070  64 00 6d 00 69 00 6e 00  69 00 73 00 74 00 72 00  |d.m.i.n.i.s.t.r.|
00000080  61 00 74 00 6f 00 72 00  73 00 0d 00 0a 00 0d 00  |a.t.o.r.s.......|
00000090  0a 00 00 00 e2 00 2a 06  39 06 31 06 4a 06 41 06  |......*.9.1.J.A.|
000000a0  20 00 39 06 45 06 44 06  4a 06 29 06 20 00 45 06  | .9.E.D.J.). .E.|
000000b0  41 06 31 06 2f 06 29 06  20 00 41 06 4a 06 20 00  |A.1./.). .A.J. .|
000000c0  45 06 44 06 41 06 20 00  2a 06 39 06 31 06 4a 06  |E.D.A. .*.9.1.J.|
000000d0  41 06 0d 00 0a 00 0d 00  0a 00 4a 06 2d 06 2f 06  |A.........J.-./.|
000000e0  2f 06 20 00 25 06 39 06  2f 06 27 06 2f 06 20 00  |/. .%.9./.'./. .|
000000f0  27 06 44 06 23 06 45 06  27 06 46 06 20 00 47 06  |'.D.#.E.'.F. .G.|
00000100  30 06 27 06 20 00 27 06  44 06 45 06 33 06 2a 06  |0.'. .'.D.E.3.*.|
00000110  2e 06 2f 06 45 06 4a 06  46 06 20 00 27 06 44 06  |../.E.J.F. .'.D.|
00000120  30 06 4a 06 46 06 20 00  4a 06 45 06 43 06 46 06  |0.J.F. .J.E.C.F.|
00000130  47 06 45 06 20 00 27 06  33 06 2a 06 2e 06 2f 06  |G.E. .'.3.*.../.|
00000140  27 06 45 06 20 00 23 06  2f 06 48 06 27 06 2a 06  |'.E. .#./.H.'.*.|
00000150  20 00 45 06 31 06 27 06  42 06 28 06 29 06 20 00  | .E.1.'.B.(.). .|
00000160  27 06 44 06 23 06 2f 06  27 06 21 06 20 00 44 06  |'.D.#./.'.!. .D.|
00000170  45 06 31 06 27 06 42 06  28 06 29 06 20 00 23 06  |E.1.'.B.(.). .#.|
00000180  2f 06 27 06 21 06 20 00  27 06 44 06 39 06 45 06  |/.'.!. .'.D.9.E.|
00000190  44 06 4a 06 27 06 2a 06  20 00 27 06 44 06 2a 06  |D.J.'.*. .'.D.*.|
000001a0  4a 06 20 00 44 06 27 06  20 00 2f 06 2e 06 44 06  |J. .D.'. ./...D.|
000001b0  20 00 44 06 44 06 46 06  38 06 27 06 45 06 00 01  | .D.D.F.8.'.E...|
000001c0  c1 ff 07 fe ff ff 3f 00  00 00 23 43 53 07 00 00  |......?...#CS...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

hda 
[/quote]

---

### Post by caljohnsmith on 2009-04-28
Apamix, it looks like you are at least booting the correct partition for Windows with Grub based on your "BOOTMGR error" and Grub configuration, but the problem is your Vista partition is missing its boot files. I would recommend following [meierfra's tutorial on fixing Vista when the boot files are missing]("http://ubuntuforums.org/showpost.php?p=5726832"). You can skip step 1 of the tutorial since your Grub's menu.lst appears to be configured correctly, the main thing is following step 2 which will copy over "bootmgr" and the Vista Boot folder to your Vista partition, and then run all the bcdedit commands to configure it correctly. Also skip the last "bootsect" command of step 2, and you can skip step 3 of the tutorial for now as it appears your Vista partition's boot sector is OK. Let me know how that goes or if you run into problems.

---

### Post by apamix on 2009-04-28
:)) Buddy that works ... many thanks :popcorn::rolleyes:

---

### Post by xoxa on 2009-09-22
Hi to everyone!

I have a problem with GRUB settings too. I've 3 OS, installed at one HDD - Win7, WinXP and Ubuntu. Now to load Win XP I have to load Win 7 loader and then choose in it "Win XP". 

When I select Windows XP from Grub menu, it says:
"BOOTMGR is missing. Press Ctrl+Alt+Del to restart".

I tried different settings in menu.lst but nothing works correctly.
Can somebody help?

There is my boot_info_script result:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /grub/stage2 and /grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdh

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       103477247 sectors, but according to the info from 
                       fdisk, it has 103492727 sectors.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda2 has 
                       104241151 sectors, but according to the info from 
                       fdisk, it has 104249244 sectors.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

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

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda6: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdh1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x17441743

Partition  Boot         Start           End          Size  Id System

/dev/sda1             206,848   103,699,574   103,492,727   7 HPFS/NTFS
/dev/sda2         103,888,896   208,138,139   104,249,244   7 HPFS/NTFS
/dev/sda3    *    208,138,140   217,905,659     9,767,520  83 Linux
/dev/sda4         217,905,660   312,576,704    94,671,045   5 Extended
/dev/sda5         217,905,723   219,865,589     1,959,867  83 Linux
/dev/sda6         219,865,653   225,729,314     5,863,662  83 Linux
/dev/sda7         225,729,378   231,593,039     5,863,662  83 Linux
/dev/sda8         231,593,103   241,360,559     9,767,457  83 Linux
/dev/sda9         241,360,623   303,853,409    62,492,787  83 Linux
/dev/sda10        303,853,473   312,576,704     8,723,232  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb03eccae

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   625,137,344   625,137,282   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb03eccaf

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   625,137,344   625,137,282   7 HPFS/NTFS


Drive: sdh ___________________ _____________________________________________________

Disk /dev/sdh: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc8eee50c

Partition  Boot         Start           End          Size  Id System

/dev/sdh1                  63   156,296,384   156,296,322   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="CE248B92248B7C69" TYPE="ntfs" 
/dev/sda2: UUID="64702D47702D2172" TYPE="ntfs" 
/dev/sda3: UUID="d9e54083-90df-4d7c-a016-0483bb42aae4" TYPE="ext3" 
/dev/sda5: UUID="84a6246e-f126-43d2-9aec-fbbcd4c11036" TYPE="reiserfs" 
/dev/sda6: UUID="4b723081-25af-45cd-90ae-6ff37487d7b3" TYPE="reiserfs" 
/dev/sda7: UUID="552ffdc5-f269-49c4-9ac7-32cae31450ed" TYPE="reiserfs" 
/dev/sda8: UUID="35982e79-2a18-4d7c-b884-0acf3c0cfd39" TYPE="reiserfs" 
/dev/sda9: UUID="6e0cca08-79bb-4315-81c6-950d5d03b3f2" TYPE="reiserfs" 
/dev/sda10: TYPE="swap" UUID="1ffc754e-efd9-4e08-9dac-574dee243b17" 
/dev/sdb1: UUID="44C00F9CC00F92FA" LABEL="Work" TYPE="ntfs" 
/dev/sdc1: UUID="64EC1E27EC1DF450" LABEL="Multimedia" TYPE="ntfs" 
/dev/sdh1: UUID="5E9052A590528405" LABEL="Mobile" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sda5 on /boot type reiserfs (rw,relatime,notail)
/dev/sda6 on /home type reiserfs (rw,relatime)
/dev/sda8 on /opt type reiserfs (rw,relatime)
/dev/sda7 on /tmp type reiserfs (rw,relatime)
/dev/sda9 on /usr type reiserfs (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/xoxa/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=xoxa)
/dev/sdh1 on /media/Mobile type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP"  /execute /fastdetect 

=========================== sda3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=d9e54083-90df-4d7c-a016-0483bb42aae4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=84a6246e-f126-43d2-9aec-fbbcd4c11036

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

# This is a divider, added to separate the menu items below from the Debian
# ones

title        Windows 7
rootnoverify    (hd0,1)
makeactive
chainloader    +1

title        Windows XP
rootnoverify    (hd0,2)
makeactive
chainloader    +1

title        Windows XP 2 - 1 0
rootnoverify    (hd0,1)
chainloader     (hd0,0)+1

title        Windows XP 2 - 1 2
rootnoverify    (hd0,1)
chainloader     (hd0,2)+1

title        Windows XP 2 - 0 0
rootnoverify    (hd0,0)
chainloader     (hd0,0)+1

title        Windows XP 2 - 0 2
rootnoverify    (hd0,0)
chainloader     (hd0,2)+1

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        84a6246e-f126-43d2-9aec-fbbcd4c11036
kernel        /vmlinuz-2.6.28-11-generic root=UUID=d9e54083-90df-4d7c-a016-0483bb42aae4 ro quiet splash 
initrd        /initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        84a6246e-f126-43d2-9aec-fbbcd4c11036
kernel        /vmlinuz-2.6.28-11-generic root=UUID=d9e54083-90df-4d7c-a016-0483bb42aae4 ro  single
initrd        /initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        84a6246e-f126-43d2-9aec-fbbcd4c11036
kernel        /memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST



=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=d9e54083-90df-4d7c-a016-0483bb42aae4 /               ext3    relatime,errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=84a6246e-f126-43d2-9aec-fbbcd4c11036 /boot           reiserfs notail,relatime 0       2
# /home was on /dev/sda6 during installation
UUID=4b723081-25af-45cd-90ae-6ff37487d7b3 /home           reiserfs relatime        0       2
# /opt was on /dev/sda8 during installation
UUID=35982e79-2a18-4d7c-b884-0acf3c0cfd39 /opt            reiserfs relatime        0       2
# /tmp was on /dev/sda7 during installation
UUID=552ffdc5-f269-49c4-9ac7-32cae31450ed /tmp            reiserfs relatime        0       2
# /usr was on /dev/sda9 during installation
UUID=6e0cca08-79bb-4315-81c6-950d5d03b3f2 /usr            reiserfs relatime        0       2
# swap was on /dev/sda10 during installation
UUID=1ffc754e-efd9-4e08-9dac-574dee243b17 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 106.7GB: boot/grub/menu.lst
 106.7GB: boot/grub/stage2
 106.7GB: boot/initrd.img-2.6.28-11-generic
 106.7GB: boot/initrd.img-2.6.28-15-generic
 106.7GB: boot/vmlinuz-2.6.28-11-generic
 106.7GB: boot/vmlinuz-2.6.28-15-generic
 106.7GB: initrd.img
 106.7GB: initrd.img.old
 106.7GB: vmlinuz
 106.7GB: vmlinuz.old

============================= sda5/grub/menu.lst: =============================

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
# kopt=root=UUID=d9e54083-90df-4d7c-a016-0483bb42aae4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=84a6246e-f126-43d2-9aec-fbbcd4c11036

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

# This is a divider, added to separate the menu items below from the Debian
# ones

title        Windows 7
rootnoverify    (hd0,1)
makeactive
chainloader    +1

title        Windows XP
rootnoverify    (hd0,2)
makeactive
chainloader    +1

title        Windows XP 2 - 1 0
rootnoverify    (hd0,1)
chainloader     (hd0,0)+1

title        Windows XP 2 - 1 2
rootnoverify    (hd0,1)
chainloader     (hd0,2)+1

title        Windows XP 2 - 0 0
rootnoverify    (hd0,0)
chainloader     (hd0,0)+1

title        Windows XP 2 - 0 2
rootnoverify    (hd0,0)
chainloader     (hd0,2)+1

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        84a6246e-f126-43d2-9aec-fbbcd4c11036
kernel        /vmlinuz-2.6.28-11-generic root=UUID=d9e54083-90df-4d7c-a016-0483bb42aae4 ro quiet splash 
initrd        /initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        84a6246e-f126-43d2-9aec-fbbcd4c11036
kernel        /vmlinuz-2.6.28-11-generic root=UUID=d9e54083-90df-4d7c-a016-0483bb42aae4 ro  single
initrd        /initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        84a6246e-f126-43d2-9aec-fbbcd4c11036
kernel        /memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST



=================== sda5: Location of files loaded by Grub: ===================


 111.7GB: grub/menu.lst
 111.7GB: grub/stage2
 111.7GB: initrd.img-2.6.28-11-generic
 111.7GB: initrd.img-2.6.28-15-generic
 111.7GB: vmlinuz-2.6.28-11-generic
 111.7GB: vmlinuz-2.6.28-15-generic
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
```

Thanks in advance!

---

### Post by zimbico on 2009-09-22
Hi xoxa,

I actually had this problem myself and fixed it before I started this thread. Unfortunately, I can't remember what program I used. Anyway, I had the same situation where booting XP from grub doesn't work, but booting XP from the Win7 bootloader does work. I'm pretty sure that I used some program to replace the necessary XP bootloader files, but can't remember the name of it. I did some googleing and came accross EasyBCD which should fix the issue:
[guide - http://neosmart.net/wiki/display/EBCD/Windows+XP]("http://neosmart.net/wiki/display/EBCD/Windows+XP")
[program - http://neosmart.net/dl.php?id=1]("http://neosmart.net/dl.php?id=1")
After getting XP to boot properly from grub, you might want to disable the Win7 bootloader menu using a program I found... I'll post again if I can find it on my computer if I still have it.
Good luck!

Brendan

EDIT: Oh, coincidence much - I used a program called.. EasyBCD! 
Ok first, boot from an XP installation CD. Press R to enter recovery mode, enter your XP's admin password, and use the command: fixmbr. That should fix your XP bootloader.
Next, install EasyBCD in Win7, Go to Add/Remove Entries, delete the xp entry then click save.
If you have any problems, you know where to come!

---

### Post by Darkwing-Duck on 2009-09-23
Why not just use GRUB to boot from all? here is a great way to get grub to do it all and fix the MBR at the same time.

[http://gwos.org/udsf/doku.php/core:grub:restore](http://gwos.org/udsf/doku.php/core:grub:restore)

---

### Post by xoxa on 2009-09-28
Hi Brendan and Darkwing Duck!
Thank you very much for your solutions. Unfortunately I have no possibilities to check them now, but I'll try both of them.

---


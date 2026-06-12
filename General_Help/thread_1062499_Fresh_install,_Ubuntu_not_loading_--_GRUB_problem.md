---
title: "Fresh install, Ubuntu not loading -- GRUB problem?"
date: 2009-02-06
forum: General Help
---

### Post by nismoskys on 2009-02-06
Hey so I've used Ubuntu quite a bit in the past, but I ditched it for a while and now I wanted to install the new 8.10, so I did.

The only OS that I'm primarily using is Windows XP.
After installing Ubuntu just now, my comp boots directly to WinXP without even showing the GRUB screen.

I believe this is because I messed with the GRUB settings back when I was using Ubuntu, but I would have thought that this fresh installation would have overwritten those previous changes.

Anyways, long story short, can someone please have a look at my GRUB file and see what I need to edit so it doesn't skip GRUB entirely and so I can select Ubuntu at the time of boot.

Thanks.  (I just pulled up the GRUB file using the install disc as a livecd)

```
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
# kopt=root=UUID=79e8ec93-c5c8-4263-b2cc-695dc736121b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=79e8ec93-c5c8-4263-b2cc-695dc736121b

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
uuid		79e8ec93-c5c8-4263-b2cc-695dc736121b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=79e8ec93-c5c8-4263-b2cc-695dc736121b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		79e8ec93-c5c8-4263-b2cc-695dc736121b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=79e8ec93-c5c8-4263-b2cc-695dc736121b ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		79e8ec93-c5c8-4263-b2cc-695dc736121b
kernel		/boot/memtest86+.bin
quiet

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
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

I appreciate the help

---

### Post by dcstar on 2009-02-07
> **nismoskys said:**
> Hey so I've used Ubuntu quite a bit in the past, but I ditched it for a while and now I wanted to install the new 8.10, so I did.

The only OS that I'm primarily using is Windows XP.
After installing Ubuntu just now, my comp boots directly to WinXP without even showing the GRUB screen.
........

When you install, the last step offers you an "Options" box (I think it is called that).

I have found in some cases you have to select it and specify a different Grub setting to the default when doing an install.

---

### Post by caljohnsmith on 2009-02-07
It looks like the issue is that you have more than one HDD, so you are currently booting a HDD that does not have Grub installed to the MBR. I would suggest going into your BIOS and change the boot order to boot another HDD and see if that works to get Grub. If not, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by nismoskys on 2009-02-08
I am pretty sure that GRUB was on the MBR of my main booting HDD, however, I dont quite remember for sure, but I may have possibly overwritten it in a recent install of WinXP? 

---
Just a little side info:
I have two HDDs, one 200GB and one 40GB.

On the 40GB is where my OS's are installed (where WinXP and Ubuntu are currently installed) and on the 160GB is where just my personal files are stored.

Anyways, here are the results from the script you suggested, sir:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

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
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x072d072d

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   394,604,594   394,604,532  83 Linux
/dev/sda2    *    394,604,595   396,709,109     2,104,515   7 HPFS/NTFS


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1a771a76

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/sdb2          40,965,750    78,075,899    37,110,150   5 Extended
/dev/sdb5          40,965,813    75,152,069    34,186,257  83 Linux
/dev/sdb6          75,152,133    78,075,899     2,923,767  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="/" UUID="41703b4b-7bb2-4820-be12-118dee106a90" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="D6346E42346E25A9" TYPE="ntfs" 
/dev/sdb1: UUID="4E3C469F3C468247" TYPE="ntfs" 
/dev/sdb5: UUID="79e8ec93-c5c8-4263-b2cc-695dc736121b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: UUID="bfd31a6e-0751-42c1-a085-04a1ce854749" TYPE="swap" 
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
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

================================ sda2/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


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
# kopt=root=UUID=79e8ec93-c5c8-4263-b2cc-695dc736121b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=79e8ec93-c5c8-4263-b2cc-695dc736121b

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
uuid		79e8ec93-c5c8-4263-b2cc-695dc736121b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=79e8ec93-c5c8-4263-b2cc-695dc736121b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		79e8ec93-c5c8-4263-b2cc-695dc736121b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=79e8ec93-c5c8-4263-b2cc-695dc736121b ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		79e8ec93-c5c8-4263-b2cc-695dc736121b
kernel		/boot/memtest86+.bin
quiet

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
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=79e8ec93-c5c8-4263-b2cc-695dc736121b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=bfd31a6e-0751-42c1-a085-04a1ce854749 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


  30.5GB: boot/grub/menu.lst
  30.5GB: boot/grub/stage2
  29.9GB: boot/initrd.img-2.6.27-7-generic
  29.9GB: boot/vmlinuz-2.6.27-7-generic
  29.9GB: initrd.img
  29.9GB: vmlinuz

=======Devices which don't seem to have a corresponding hard drive==============

 sdc .
 sdd .
 sde .
 sdf .

```

Thanks again

---

### Post by caljohnsmith on 2009-02-08
OK, from the Live CD, how about doing:
```
sudo grub
grub> root (hd1,4)
grub> setup (hd1)
grub> quit
```
That will install Grub to the MBR of your sdb Windows/Ubuntu drive, because currently Grub is just installed to the MBR of your sda data drive. Also, your menu.lst will need a little tweaking:
```
sudo mount /dev/sdb5 /mnt && gksudo gedit /mnt/boot/grub/menu.lst
```
And then replace both your Windows entries at the end of the file with:
```
title Windows XP
root (hd0,0)
chainloader +1
```
Reboot, and let me know how far you get. We can work from there if necessary.

---

### Post by nismoskys on 2009-02-08
It worked perfectly :) I'm now posting from the installed Ubuntu.
I haven't tried booting up WinXP yet but I hope it will work properly.

I would also like to adjust the time delay and order of the GRUB screen but I'll save you the trouble and search on it first :)

Thanks a lot for your help though, I really appreciate it. This is what keeps Ubuntu going :)

---

### Post by nismoskys on 2009-02-08
I searched and, of course, figured out that the time delay and order of GRUB are easily changed with the 'default' and 'timeout' settings in the menu.lst file so that worked great.

I also booted up into XP and it loaded up fine as well.

So it seems I'm all set. Once again, thanks for the help.

---

### Post by caljohnsmith on 2009-02-08
Glad to hear it's all working and you figured out how to use the "timeout" and "default" lines. Cheers and have fun with Ubuntu and Windows. :)

---

### Post by nismoskys on 2009-02-14
Please help.... The power went out the other day when I wasn't home and I came home to find that my comp wouldn't turn on at all.
I swapped in another power supply and got it to turn on but i was getting Grub error 21.

I loaded up the super grub cd and did some stuff without knowing what i was really doing, then i booted up and got a message from windows saying it couldnt boot.

so here I am in live cd and now I think that my second (40GB) harddrive where my OSs are installed is not being recognized at all?

i just ran that boot script again...

```
============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x072d072d

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   394,604,594   394,604,532  83 Linux
/dev/sda2    *    394,604,595   396,709,109     2,104,515   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="/" UUID="41703b4b-7bb2-4820-be12-118dee106a90" TYPE="ext3" 
/dev/sda2: UUID="D6346E42346E25A9" TYPE="ntfs" 
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
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)

================================ sda2/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=======Devices which don't seem to have a corresponding hard drive==============

 sdb .
 sdc .
 sdd .
 sde .

```

//where's my SDB??

---

### Post by caljohnsmith on 2009-02-14
Looks like you unfortunately have hardware problems, because your sdb drive isn't even detected by Ubuntu any more. So you can't even boot your sda Windows drive and get into Windows either? I would recommend pulling out the sdb drive and plug it into another computer just to see if it still works. If it does, the problem is most likely with your computer then. If not, then you might have to say goodbye to that HDD. Good luck and let me know how it goes.

---

### Post by nismoskys on 2009-02-15
I really appreciate your quick responses caljohnsmith.

Yes, unfortunately I had to say goodbye to that HDD. 
I don't know how this power outage killed my power supply AND HDD, this has never happened to me before... any suggestions to prevent it in the future, short of getting a UPS? 

I'm just very grateful that the HDD with all of my important data didnt get messed up and just as grateful that I happened to have a spare power supply and harddrive laying around.

I've since reinstalled XP and Intrepid Ibex on the spare HDD I found and I am back in business :) , although I've lost all of my OS settings and have to reinstall programs, drivers (for XP) and such. The important thing is, however, that I still have my data.

Thanks again caljohnsmith, for all your help.

---

### Post by caljohnsmith on 2009-02-15
You're certainly welcome, and I'm really glad to hear that you didn't lose anything too valuable as far as your data is concerned; you are very fortunate. Good luck, and hope customizing your new Ubuntu install the way you like it goes smoothly. :)

---

### Post by damagemanual on 2009-03-09
Hey guys,

I'm having the same issue with Grub. It just hangs at Grub_ after a fresh install of 8.10. This system also has a fresh load of XP as well.

Any ideas how to resolve this?

Thanks
-Seth

I've attached both the menu.lst and the results of the boot_info_script.

Any help would be great!

---

### Post by meierfra. on 2009-03-09
According to results from the Boot Info Script, grub seems to be configured correctly.  This might be one of the rare cases where grub does not work, when it's installed in the MBR.  I'm not sure that this will cure your problem, but lets see what happens if you install Grub to the boot sector of the ubuntu partition.

Boot from the Ubuntu  Live CD, open a terminal and type

```
sudo grub
```
and at the grub prompt:

```
root  (hd0,4)
setup (hd0,4)
quit
```

The next couple of  lines of code will install a Windows-style MBR and set the Boot flag to the Ubuntu partition:

```
sudo lilo -M /dev/sda ext
sudo lilo -A /dev/sda 5
```

(depending on your LiveCD you might have to first install "lilo"  via "sudo apt-get install lilo" for this to work.)

Reboot and hope for the best.

---

### Post by damagemanual on 2009-03-09
That works, thanks very much!

---

### Post by meierfra. on 2009-03-09
> That works, thanks very much!
It was a shot in the dark,  so I'm really glad it worked. Have fun with XP and Ubuntu.

---

### Post by leoman.49 on 2009-06-11
Hi Every one ,, 

I am facing the problem with the Grub loading the installed Ubuntu-8.10
previously i installed XP and now overrided with Ubuntu-8.10

But i am unable to login to installed Ubuntu-8.10
here is the result which i got after running script 

Wating for the reply......



============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x03e4de94

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   150,288,074   150,288,012  83 Linux
/dev/sda2         150,288,075   156,296,384     6,008,310   5 Extended
/dev/sda5         150,288,138   156,296,384     6,008,247  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="9c165205-d282-43c3-8de7-6015a5b9edb2" TYPE="ext3" 
/dev/sda5: UUID="8b865536-86ac-4c7e-8d0b-f63ddb35ce7c" TYPE="swap" 
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
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# kopt=root=UUID=9c165205-d282-43c3-8de7-6015a5b9edb2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9c165205-d282-43c3-8de7-6015a5b9edb2

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


title Ubuntu, kernel 2.6.27-7-generic
root (hd0,2)
kernel /boot/vmcoreinfo-2.6.27.7-generic root=UUID=9c165205-d282-43c3-8de7-6015a5b9edb2 ro quiet splash rootflags=data=writeback locale=nl_NL
initrd /boot/initrd.img-2.6.27-7-generic
quiet

title Ubuntu, kernel 2.6.27-7-generic (recovery mode)
root (hd0,2)
kernel /boot/vmcoreinfo-2.6.27.7-generic root=UUID=9c165205-d282-43c3-8de7-6015a5b9edb2 ro single rootflags=data=writeback
initrd /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        9c165205-d282-43c3-8de7-6015a5b9edb2
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9c165205-d282-43c3-8de7-6015a5b9edb2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=8b865536-86ac-4c7e-8d0b-f63ddb35ce7c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  40.3GB: boot/grub/menu.lst
  40.3GB: boot/grub/stage2
  40.3GB: boot/initrd.img-2.6.27-7-generic
  40.3GB: initrd.img

---


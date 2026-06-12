---
title: "Ubuntu Does Not Boot But Machine Goes Into A Test Mode"
date: 2009-06-16
forum: General Help
---

### Post by james.brantley on 2009-06-16
[SIZE=4]I am unable to boot into Unbuntu. I have a dual boot system with Vista. When my machine restarts and I am presented with the option to boot into Vista or Ubuntu I choose Ubuntu but instead of the OS booting it will always go into some type of test mode, only when I choose Ubuntu. If I choose Vista it will properly boot into that OS, but I do not want to use Vista. Thanks for any help![/SIZE]

---

### Post by blueridgedog on 2009-06-16
Could the test mode possibly be your monitor simply lacking signal?  Do you hear any sound from the system when you attempt to boot Ubuntu?  When it is in this test mode, is there any activity on the hard drive (looking at the light on the case)?

---

### Post by james.brantley on 2009-06-16
> **blueridgedog said:**
> Could the test mode possibly be your monitor simply lacking signal? Do you hear any sound from the system when you attempt to boot Ubuntu? When it is in this test mode, is there any activity on the hard drive (looking at the light on the case)?
 
[SIZE=3]There is signal to the monitor, I **know** it is in a test mode because it states what number test it is in at a given time. In the upper left hand corner of the blue screen it has my processor type and various other info about my machine. There is a series of 4 test I believe and when it is done it states that no problems have been found and prompts me to restart the machine, I restart the machine, choose Ubuntu and it will always go into the offending test mode. I have been all over the net and in numerous forums and I have not been able to find any assistance. This has been going on for about the last seven hours and I am beginning to think that I will just have to reformat my machine and start over from scratch, which I really do not want to do because after about a month of tweaking things I had got Ubuntu looking and acting just like I wanted. I am so frustrated and almost to my whits end! [/SIZE]

---

### Post by lindsay7 on 2009-06-16
Sounds like it is starting up with Memtest, can you post the output of 


sudo gedit /boot/grub/menu.lst  that is the letter l not the number 1, also post the output of 

sudo fdisk -l  again the letter l

this will tell us what is on your grub menu and how you drives are configured.

---

### Post by james.brantley on 2009-06-16
> **lindsay7 said:**
> Sounds like it is starting up with Memtest, can you post the output of 
 
 
sudo gedit /boot/grub/menu.lst that is the letter l not the number 1, also post the output of 
 
sudo fdisk -l again the letter l
 
this will tell us what is on your grub menu and how you drives are configured.
 
[SIZE=3]I can not access the terminal as I an unable to boot into Ubuntu at all. I am in a really bad way. I have had to resort back to using Windows which I am not very pleased with![/SIZE]

---

### Post by blueridgedog on 2009-06-16
Good catch on memtest...can you boot off of a live cd and post the output of the command?

---

### Post by james.brantley on 2009-06-16
> **blueridgedog said:**
> Good catch on memtest...can you boot off of a live cd and post the output of the command?
 
[SIZE=3]I will try, it won't affect my current Ubuntu installation will it? [/SIZE]

---

### Post by alienkid10 on 2009-06-16
It shouldn't

---

### Post by james.brantley on 2009-06-16
> **alienkid10 said:**
> It shouldn't
 
[SIZE=3]Thanks, here I go[/SIZE]

---

### Post by james.brantley on 2009-06-16
[SIZE=3]When I boot from the live cd it put me into what appears to be fresh install of ubuntu. I don't think it will help but here is the results of the commands that were posted.

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x39d23778

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29189   234457056+   7  HPFS/NTFS
/dev/sda2           29189       30402     9739264    7  HPFS/NTFS

Disk /dev/sdb: 2000 MB, 2000748032 bytes
64 heads, 63 sectors/track, 969 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         969     1953439+   7  HPFS/NTFS

[/SIZE]

---

### Post by lindsay7 on 2009-06-16
Can you post the results of 

sudo gedit /boot/grub/menu.lst

I do not see the Ubuntu installation in what you posted. The results of the sudo gedit command will tell us more.

---

### Post by wpshooter on 2009-06-16
> **blueridgedog said:**
> Good catch on memtest...can you boot off of a live cd and post the output of the command?

I don't think the way he is describing this that this is Memtest.

Unless, Memtest has changed recently, wouldn't it just continue to run endlessly until **_he stopped it_** ?

---

### Post by james.brantley on 2009-06-16
[SIZE=3]Okay, live cd insterted again-option are reboot now, reboot later and help me boot from cd. When I choose reboot now it reverts back to the previous three options, when I choose the other two it tells me that a previous installation must be removed before proceeding. I tried again to boot into Ubuntu and it still goes into memtest (I agree and believe that is the "offending test") It doesn't appear that I can access the current installation of Ubuntu in any way. I will explore the live cd options again but I am fairly sure that I tried all options. I am way frustrated! Thanks for the help folks, I just can't give up on this and reinstall, that would be total defeat![/SIZE][SIZE=3]

[/SIZE]

---

### Post by lindsay7 on 2009-06-16
Are you starting the computer with the Ubuntu live cd in the drive and powering on your computer?

You should start up with the live cd and the screen will look like the installed version.  You just need to go to the terminal and type in the commands. Note you can access Firefox and email from there with the results, using copy and paste.

Is your computer bios set to boot from a cd. If not you need to press the del key or the f2 key to get into your bios and set it to boot from the cd drive first.

---

### Post by james.brantley on 2009-06-16
> **wpshooter said:**
> I don't think the way he is describing this that this is Memtest.
 
Unless, Memtest has changed recently, wouldn't it just continue to run endlessly until **_he stopped it_** ?
 
 
 [SIZE=3]It does eventually come to an end. When I restart after completion it just goes back into the test. The screen is blue characters are white. The test progress is shown in the upper right of the screen and I think there are four stages of said test if I am correct. There is an option to change configurations but only the configuration of the test itself. Maybe this could help someone identify it!  [/SIZE]

---

### Post by wpshooter on 2009-06-16
Hold on a second and let me reboot and take a look at Memtest.  It has been a while since I have had to run it.  Be right back.

If it is Memtest, then it will have Memtest 86+ in black lettering on a green background in the very top left hand corner of the screen.

---

### Post by james.brantley on 2009-06-16
> **lindsay7 said:**
> Are you starting the computer with the Ubuntu live cd in the drive and powering on your computer?
 
You should start up with the live cd and the screen will look like the installed version. You just need to go to the terminal and type in the commands. Note you can access Firefox and email from there with the results, using copy and paste.
 
Is your computer bios set to boot from a cd. If not you need to press the del key or the f2 key to get into your bios and set it to boot from the cd drive first.
 
[SIZE=3]Actually I was "restarting" with the cd in. My computer is not set to boot from cd. I will do this now. [/SIZE]

---

### Post by wpshooter on 2009-06-16
> **james.brantley said:**
> [SIZE=3]Actually I was "restarting" with the cd in. My computer is not set to boot from cd. I will do this now. [/SIZE]


Once you get that done, please when you reboot to the Ubuntu CD, humor me and test the integrity of the Ubuntu CD by running the verification function which is found on the initial Ubuntu boot screen menu.

Thanks.

---

### Post by james.brantley on 2009-06-16
> **wpshooter said:**
> Once you get that done, please when you reboot to the Ubuntu CD, humor me and test the integrity of the Ubuntu CD by running the verification function which is found on the initial Ubuntu boot screen menu.
 
Thanks.
 
[SIZE=3]Alright, I checked the integrity, results-[/SIZE]
 
[SIZE=3]"no errors found press any key to reboot"[/SIZE]
[SIZE=3][/SIZE] 
[SIZE=3]I did however verify that it is memtest, I choose "test memory" from the initial installation screen and it went into the test that my machine goes into instead of booting to Ubuntu.[/SIZE]

---

### Post by lindsay7 on 2009-06-16
Ok, great, it least we know what is going on, now that you can boot with the live cd please post the following


sudo gedit /boot/grub/menu.lst that is the letter l not the number 1, also post the output of

sudo fdisk -l again the letter l

---

### Post by louieb on 2009-06-16
From the looks of the fdisk output seems you have used  WUBI (inside windows) to install Ubuntu.  

If thats true don't think you can fix it the same way you would fix a normal install.  At this point don't even know if the problem is with Vista's boot loader or with Ubuntu.

After checking the live CD for defects Please follow the instructions in this post   [Boot Info Script Instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3") and post the results.txt file back here.

---

### Post by james.brantley on 2009-06-16
I did use Wubi.


=```
============================ Boot Info Summary: ==============================

 => HP/Gateway is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /bootmgr /Boot/BCD 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOT/BCD

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x39d23778

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   468,914,175   468,914,113   7 HPFS/NTFS
/dev/sda2         468,914,176   488,392,703    19,478,528   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000 MB, 2000748032 bytes
64 heads, 63 sectors/track, 969 cylinders, total 3907711 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                 129     3,907,007     3,906,879   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="88FED00FFECFF38A" LABEL="COMPAQ" TYPE="ntfs" 
/dev/sda2: UUID="A8B2D2B2B2D2846A" LABEL="FACTORY_IMAGE" TYPE="ntfs" 
/dev/sdb1: UUID="C80CA47B0CA46662" LABEL="JBRANTLEY 1" TYPE="ntfs" 

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
/dev/sdb1 on /media/JBRANTLEY 1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


==================== sda1/ubuntu/disks/boot/grub/menu.lst: ====================

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
default saved

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
# kopt=root=UUID=88FED00FFECFF38A loop=/ubuntu/disks/root.disk ro

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=88FED00FFECFF38A loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=88FED00FFECFF38A loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
root        ()/ubuntu/disks
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
chainloader    +1


======================== sda1/ubuntu/winboot/menu.lst: ========================

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

================================== sda1Wubi: ==================================

Operating System: "Ubuntu 9.04"

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

=================== sda1: Location of files loaded by Grub: ===================


  44.0GB: ubuntu/disks/boot/grub/menu.lst
  43.9GB: ubuntu/disks/boot/initrd.img-2.6.28-11-generic
  43.8GB: ubuntu/disks/boot/vmlinuz-2.6.28-11-generic
```

---

### Post by james.brantley on 2009-06-16
[SIZE=3]Just to fill you all in a bit, my problem started when I installed a package from synaptic that would allow me to change my boot sequence via a GUI, I ran the app and chose the Ubuntu I thought was the proper one. There were four or five of them, one was "generic" one was "kernel" one was only numbers but was grouped with the Ubuntu items and I am not sure what the last one or two were. After I chose and rebooted is when my machine went into the eternal memtest loop.[/SIZE]

---

### Post by lindsay7 on 2009-06-16
Sounds like you installed the "Startup Manager" application, does that sound familiar?

---

### Post by james.brantley on 2009-06-16
> **lindsay7 said:**
> Sounds like you installed the "Startup Manager" application, does that sound familiar?
 
[SIZE=3]It does sound remotely familiar. I installed so many packages from synaptic in the last month. It would not be anything to do with [Vista Boot Pro]("http://www.vistabootpro.org/") that I installed (in Windows) earlier today would it? I thought this software would help me solve my issue but it did not discover my Ubuntu installation. The program was supposed once again give you a GUI to change the boot sequence. I really should have just stuck with the terminal, I imagine I could have changed the boot sequence that way but I tried to take the easy way out.[/SIZE]

[SIZE=3]*The more I think about it the more familiar "startup manager" sounds. Does this complicate matters any more than they already are?[/SIZE]

---

### Post by lindsay7 on 2009-06-16
Well, that may explain part of what is going on.  If you were having boot problems before you installed this, my guess and it is a guess, is that installing that program change deleted your windows/Ubuntu boot loader. I have not worked on the Wubi installation and booting process, so I can not help you at this time. 

I am going to get out of the way and someone who knows the Wubi install process to give you some direction.  Good luck and I will watch how this goes for you.

I just saw you edit, it could be that you could try to uninstall the "Startup-Manager" program. If for some reason you had it set to only start or made the memtest the start up option, it could be giving you only that at start up.

You could try typing sudo apt-get remove startup-manager in the terminal.

---

### Post by james.brantley on 2009-06-16
> **lindsay7 said:**
> Well, that may explain part of what is going on. If you were having boot problems before you installed this, my guess and it is a guess, is that installing that program change deleted your windows/Ubuntu boot loader. I have not worked on the Wubi installation and booting process, so I can not help you at this time. 
 
I am going to get out of the way and someone who knows the Wubi install process to give you some direction. Good luck and I will watch how this goes for you.
 
[SIZE=3]Thanks for your time lindsay7. I really appreiciate it![/SIZE]

---

### Post by DeMus on 2009-06-16
In your menu.lst file I see this:
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default saved

```
Change the last line into
default 0

You have to boot from the cd to be able to do that.

---

### Post by james.brantley on 2009-06-16
[quote=louieb;7470163]From the looks of the fdisk output seems you have used WUBI (inside windows) to install Ubuntu. 
 
[SIZE=3]Seeing as I did use Wubi to install Ubuntu, do you have any other ideas louieb? [/SIZE]

---

### Post by james.brantley on 2009-06-16
> **DeMus said:**
> In your menu.lst file I see this:
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default saved

```
Change the last line into
default 0
 
You have to boot from the cd to be able to do that.
 
[SIZE=3]I going to give it a try right now, thanks![/SIZE]

---

### Post by james.brantley on 2009-06-17
> **DeMus said:**
> In your menu.lst file I see this:
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default saved

```Change the last line into
default 0

You have to boot from the cd to be able to do that.

[SIZE=3]I am unable to edit this as I am only able to view it via this script** home/ubuntu/Desktop/boot_info_script032.sh **which displays the results as a text file.[/SIZE]

---

### Post by james.brantley on 2009-06-17
[SIZE=3]I have ran**sudo gedit /boot/grub/menu.lst** again and clicked  the open options and it gave me the following info, is there any way I can edit the entries? These are the options I was presented with when I was choosing which to boot into via the GUI I installed from synaptic. I must have inadvertenly chose the memtest! I guess I was not paying as close attention as I should have been, maybe in a bit of a rush to change my boot sequence.[/SIZE]

[SIZE=3]These are the listings in the boot folder:

[B]abi-2.6.28-11-generic
config-2.6.28-11-generic
memtest86+.bin
vmcoreinfo-2.6.28-11-generic

[/B] I can open these and view data,but I have no idea what to edit or if I am even at a point where I can edit it. I have been on this problem now for about 12 hours and I am almost ready to just reformat my drive! 

Is there any way I can choose from the boot folder which option to boot into?


[/SIZE]

---

### Post by james.brantley on 2009-06-17
[SIZE=3]This is the data within the first option which is
[/SIZE][SIZE=3]**abi-2.6.28-11-generic **there is a lot of data here and I am not sure if it will help anyone help me or not.[/SIZE]
[SIZE=3]
EXPORT_SYMBOL arch/x86/kernel/scx200 0x254e5667    scx200_gpio_base
EXPORT_SYMBOL arch/x86/kernel/scx200 0x35a3c008    scx200_gpio_configure
EXPORT_SYMBOL arch/x86/kernel/scx200 0x8cfa375c    scx200_gpio_shadow


EXPORT_SYMBOL_GPL vmlinux 0xffc21f5a    relay_reset
EXPORT_SYMBOL_GPL vmlinux 0xffdb65dc    part_round_stats
EXPORT_SYMBOL_GPL vmlinux 0xfff51481    dm_noflush_suspending
EXPORT_UNUSED_SYMBOL vmlinux 0x00000000    init_mm
EXPORT_UNUSED_SYMBOL vmlinux 0x00000000    simple_prepare_write

**I removed the center of this data as it was multiple pages, I can post it if someone feels it may be of assistance.**
[/SIZE]

---

### Post by james.brantley on 2009-06-17
[SIZE=3]Would** Common config options automatically generated by splitconfig.pl** tell me anything???[/SIZE]
[SIZE=3][/SIZE] 
[SIZE=3]**I am stuck.**[/SIZE]

---

### Post by james.brantley on 2009-06-17
**[SIZE=4]Help anyone, please!!!![/SIZE]**

---

### Post by louieb on 2009-06-17
Haven't used WUBI.  so this is just a guess based on the fact you have **hiddenmenu **turned on.
```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

``` Right after you choose Ubuntu start pressing the **<ESC>** key and see if that brings up the GRUB menu. 

Should be able to boot Ubuntu and get the GRUB defaults straightened out from there.

---

### Post by louieb on 2009-06-17
On another note: You can get to your wubi install and fix it from a live CD. Its more work than accessing a partition install and is described here.
[https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?]("https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?")

---

### Post by wpshooter on 2009-06-17
James:

If it were me, I would consider trying to save/backup any important information that I had on either my Windwos install or my Ubuntu install (although may not be possible) and then WIPE the drive completely clean and then first reinstall Windows from scratch and after that, do an install of Ubuntu from the bootable Ubuntu CD (not from within Windows).  I think you will windup with a much more stable/dependable dual boot system this way and you will also probably windup spending much less time doing this than in the effort that it is going to take you to try to fix this piece-meal and thereby run the risk of having further problems down the road.

Good luck.

---

### Post by lindsay7 on 2009-06-17
> **wpshooter said:**
> James:

If it were me, I would consider trying to save/backup any important information that I had on either my Windwos install or my Ubuntu install (although may not be possible) and then WIPE the drive completely clean and then first reinstall Windows from scratch and after that, do an install of Ubuntu from the bootable Ubuntu CD (not from within Windows).  I think you will windup with a much more stable/dependable dual boot system this way and you will also probably windup spending much less time doing this than in the effort that it is going to take you to try to fix this piece-meal and thereby run the risk of having further problems down the road.

Good luck.


My thoughts too.  You might try to uninstall your wubi install from the windows control panel first and see if windows boots the way you want it and then do the dual boot Ubuntu install with a true dual boot not wubi.



Here are some web sites to help you get a new Ubunu install set up and going. There are some redundancies here but you will get the idea.

If you have problems with this, then do the reformat and setup windows first and them the Ubuntu install.  You will be much happier with a true dual boot then the wubi install.


[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-810-intrepid-ibex.html)



[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)


[http://www.dailygyan.com/2008/11/10-things-you-should-do-immediately.html](http://www.dailygyan.com/2008/11/10-things-you-should-do-immediately.html)


[http://www.danielandrade.net/2007/11/10/10-things-to-do-just-after-installing-ubuntu-710/](http://www.danielandrade.net/2007/11/10/10-things-to-do-just-after-installing-ubuntu-710/)


[http://ubuntuforums.org/showthread.php?t=380527](http://ubuntuforums.org/showthread.php?t=380527)


[http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html](http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html)


[http://www.unix-tutorials.com/go.php?id=4054](http://www.unix-tutorials.com/go.php?id=4054)

---

### Post by james.brantley on 2009-06-17
[SIZE=3]Alright, I am at it once again. **Thank you** folks for helping me out with this issue. I am going to take the given advice and totally start from scratch. Stability was one of my main attrctions to Linux, Ubuntu and I need to do things right. It appears that Wubi might not be the best way to go about things. It does serve it's purpose of getting more converts I think. Yes I am going to create a true dual boot! Once again I'd just like to say thanks to all those that assisted me. [/SIZE]

---

### Post by james.brantley on 2009-06-17
[SIZE=3]I shall return!![/SIZE]

---

### Post by raymondh on 2009-06-17
hello James.Brantley,

Some links for reference as you prepare for dual-boot

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=BasicCommands](https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=BasicCommands)
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)
[http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm](http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm)
[http://wiki.linuxquestions.org/wiki/GRUB](http://wiki.linuxquestions.org/wiki/GRUB)

Good luck.

---

### Post by james.brantley on 2009-06-17
[SIZE=3]Thanks for the links! I'm off to start this project over! Well I suppose I need to wait for my download to complete. 23%[/SIZE]

---

### Post by wpshooter on 2009-06-17
> **james.brantley said:**
> [SIZE=3]I shall return!![/SIZE]

Your real name is not Douglas McArthur, is it ???:)

---

### Post by raymondh on 2009-06-17
> **wpshooter said:**
> Your real name is not Douglas McArthur, is it ???:)

:)  We must be of the same generation (or next to each other's) to reference that phrase quickly with a name.  'Said prior to departing The Philippines for Australia as well as upon return on Leyte Beach.

---

### Post by lindsay7 on 2009-06-17
Hey, I thought I was the only one to catch this. haha

You, mean I am not the only over the hill person on this forum?  Next thing will be people who remember "If you can't take the heat.. get out of the kitchen!"

---

### Post by james.brantley on 2009-06-17
[SIZE=3]Haha, I feel right at home now! My Vista install has just completed, just though I'd check in quick and see if there were any futher posts. I am going to install my Ubuntu now. Almost done![/SIZE]

---

### Post by lindsay7 on 2009-06-17
If you like, set up a / partition which will be for the Ubuntu system and a /home partition which will be for all you data and stuff. Ubuntu will set up a swap partition automatically.

Having the separate /home partition will let you upgrade to future versions of ubuntu and not cop[y over or delete what you have.

Use the manual option and set the mount points and partitons as / and /home.

---

### Post by lindsay7 on 2009-06-17
Here is how my system looks,


[ATTACH]117987[/ATTACH]

---

### Post by james.brantley on 2009-06-17
> **lindsay7 said:**
> If you like, set up a / partition which will be for the Ubuntu system and a /home partition which will be for all you data and stuff. Ubuntu will set up a swap partition automatically.
 
Having the separate /home partition will let you upgrade to future versions of ubuntu and not cop[y over or delete what you have.
 
Use the manual option and set the mount points and partitons as / and /home.
 
[SIZE=3]This is what I would like to do. Do I set this up prior to my install of Ubuntu? When I am setting the partition for Ubuntu? This is my second attempt at installation without Wubi. After my first attempt I could not even get synaptic to operate correctly. When I ran it I got an error saying that there was not enough disk space to update. Also ran update manager and I got the error "**failed to run /user/sbin/synaptic unable to copy users xauthorization file**". I also was getting some type of error for everything I tried. I really don't want to use Wubi again and I want to make my next upgrade as easy as it can be. I will hold off before I try install it the proper way again. (without Wubi) AT this point in time I have a fresh install of Vista. I have not yet started the Ubuntu phase yet. I think maybe I might wait and do some more reading. I do think that my issue might have been I did not choose the "guide resize" option when the partion was being created. Might that be why I was out of space. I have a 350GB drive so it seems to that there would be plenty of space. ALso I am not very clear on creating the /home partion. [/SIZE]

---

### Post by lindsay7 on 2009-06-18
Did you set up any partitions before you loaded Windows? If you did how big a partition did you leave for Ubuntu. If you did not, you can use the windows disk manager to shrink your windows parition and make one or more new partitions. Be sure to run defrag in windows to make sure there are no problems with doing this partitioning. I would make three partitions to prepair for your Ubuntu installation. And I would just format them fat32 in windows (it formats faster I think), later the Ubuntu install will format them as you choose, ext3 is fine, the new ext4 is good too but it is new but faster, so you decide.  

Once you have the partitions set up then start the Ubuntu install and when you get to the point of choosing where and how you want to install, choose the manual option. You should see the windows installation at the front of the drive and the three partitions that you have set up. I would make the first partition about 10 to 15 gigs. This you will mount a the "/" partition and this is where the system goes. Choose to format it ext3 or ext4.  The second partition should be large ( how big is up to you but 50 gigs and up is good. Mount this partition as "/home" this is where all your data and other stuff you want to keep will go. Format it the same as the other partition ext3 or ext4. The last partition should be mounted as the "swap" partition and should be 5 to 8 gigs. I do not think you have to pick a format as the install will do that itself. The swap partion does not need to be any larger that the 5 to 8 gigs,  The /home partition is the one that you want to have as the largest.

There will be columns to set the mount points and a box to mark format or not and also a choice for the formate type.

That is the basics in a nut shell, it is easier when you see it then it sounds. If you get stuck just ask for help.

I think I covered it all, if not someone will point it out.

After you set up the one large partition for you Ubuntu install. then get out of windows and use the Gparted program to do the other Ubuntu partitions. Download the Gparted program form their web side and burn it to a cd. It will be bootable and it is easier to work with since all the partitions and drives will be unmounted. It is good to have it around anyway. When you have the partitions all set then use the Ubuntu live cd to do the installation, again choose the manual option.


This should give you the idea,


[http://beginlinux.com/desktop_training/ubuntu/1073-ubuntu-intrepid-ibex-install](http://beginlinux.com/desktop_training/ubuntu/1073-ubuntu-intrepid-ibex-install)

---

### Post by james.brantley on 2009-06-18
> **lindsay7 said:**
> After you set up the one large partition for you Ubuntu install. then get out of windows and use the Gparted program to do the other Ubuntu partitions. Download the Gparted program form their web side and burn it to a cd. It will be bootable and it is easier to work with since all the partitions and drives will be unmounted. It is good to have it around anyway. When you have the partitions all set then use the Ubuntu live cd to do the installation, again choose the manual option.
 
 
This should give you the idea,
 
 
[http://beginlinux.com/desktop_training/ubuntu/1073-ubuntu-intrepid-ibex-install](http://beginlinux.com/desktop_training/ubuntu/1073-ubuntu-intrepid-ibex-install)
 
[SIZE=3]Good morning and thank you for partition info. I did not do any partitioning yesterday, just installed Windows and then moved on to the Ubuntu bootable cd. I am getting started right away, well after I do a little reading. I want to make sure time around the installation successful! After using primarily Ubuntu for over a month now it is not too plesant having to use Vista. One question though, isn't the live cd the one that contains Wubi?[/SIZE]

---

### Post by DeMus on 2009-06-18
> **james.brantley said:**
> [SIZE=3]Good morning and thank you for partition info. I did not do any partitioning yesterday, just installed Windows and then moved on to the Ubuntu bootable cd. I am getting started right away, well after I do a little reading. I want to make sure time around the installation successful! After using primarily Ubuntu for over a month now it is not too plesant having to use Vista. One question though, isn't the live cd the one that contains Wubi?[/SIZE]

Don't start with Wubi, but do a nice clean fresh install side by side with Windows. You get the Grub boot menu and choose (or wait 10 seconds to let the system choose) Ubuntu.
When using Wubi you still depend on Windows. Imagine it crashes, not uncommon, you will also loose your ubuntu installation.
Just go for the dual boot, you'll love it.

---

### Post by james.brantley on 2009-06-18
[SIZE=3]I just tried to shrink the first partition and was told there was not enough disk space to complete the operation.[/SIZE]
[SIZE=3]Here is the way things are set up as default after a fresh install of Vista.[/SIZE]
 
[SIZE=3][/SIZE] 
[SIZE=3][/SIZE] 
[SIZE=3][/SIZE]

---

### Post by james.brantley on 2009-06-18
> **DeMus said:**
> Don't start with Wubi, but do a nice clean fresh install side by side with Windows. You get the Grub boot menu and choose (or wait 10 seconds to let the system choose) Ubuntu.
When using Wubi you still depend on Windows. Imagine it crashes, not uncommon, you will also loose your ubuntu installation.
Just go for the dual boot, you'll love it.
 
[SIZE=3]The last thing I want to do is use Wubi again! I'm right now trying to get this partitioning issue taken care of so I can do this the way it should be done! No short cuts![/SIZE]

---

### Post by DeMus on 2009-06-18
> **james.brantley said:**
> [SIZE=3]I just tried to shrink the first partition and was told there was not enough disk space to complete the operation.[/SIZE]
[SIZE=3]Here is the way things are set up as default after a fresh install of Vista.[/SIZE]
 
[SIZE=3][/SIZE] 
[SIZE=3][/SIZE] 
[SIZE=3][/SIZE]

Before shrinking the Vista partition you might consider do a defrag first. The OS will try to put files to the front of the partition, although this does not always happen.
When this succeeds you can shrink the C partition to give Ubuntu let's say 50GB or so. This is enough to have a nice setup.

---

### Post by james.brantley on 2009-06-18
[SIZE=3]Question- do I need to assign the new partion a seperate drive letter or a new path?[/SIZE]

---

### Post by DeMus on 2009-06-18
> **james.brantley said:**
> [SIZE=3]Question- should I assign the new partion a seperate drive letter?[/SIZE]

No, don't make a partition at all. Just keep the space empty. Then, when installing Ubuntu, you can choose (in step 4 of the installation process) to use the empty space.
Make sure you place the grub bootloader on the mbr of your (only) harddisk hd0.

---

### Post by james.brantley on 2009-06-18
[SIZE=3]Okay, I have Ubuntu reinstalled but I could not shrink the Vista partition small enough to allow me to retain at least 60 GB for /home and still have enough left to create two more partitions. So I assume this means my data and my system will be on the same partition correct? Will I still be able to upgrade my system without effecting my data? This is what things look like. Should I try this again before I go any further?

[/SIZE]```
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
timeout        10

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
# kopt=root=UUID=35a481f7-b9a1-4785-aca5-69c12d8a6dfa ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=35a481f7-b9a1-4785-aca5-69c12d8a6dfa

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

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        35a481f7-b9a1-4785-aca5-69c12d8a6dfa
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=35a481f7-b9a1-4785-aca5-69c12d8a6dfa ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        35a481f7-b9a1-4785-aca5-69c12d8a6dfa
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=35a481f7-b9a1-4785-aca5-69c12d8a6dfa ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        35a481f7-b9a1-4785-aca5-69c12d8a6dfa
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=35a481f7-b9a1-4785-aca5-69c12d8a6dfa ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        35a481f7-b9a1-4785-aca5-69c12d8a6dfa
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=35a481f7-b9a1-4785-aca5-69c12d8a6dfa ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        35a481f7-b9a1-4785-aca5-69c12d8a6dfa
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title        Windows Vista (loader)
rootnoverify    (hd0,3)
savedefault
makeactive
chainloader    +1

```[SIZE=3]
[/SIZE]

---

### Post by james.brantley on 2009-06-18
[SIZE=3]It's so nice to back! (To Ubuntu). I am going to leave things the way the are for now and read more and more in depth, then try it again and some how force the Vista partition to be smaller and thus have my system on its own partition. Thanks for your  help everyone![/SIZE]

---

### Post by james.brantley on 2009-06-18
[SIZE=3]My entire system seems to be running faster than when installed under Wubi.[/SIZE]

---

### Post by DeMus on 2009-06-18
> **james.brantley said:**
> [SIZE=3]My entire system seems to be running faster than when installed under Wubi.[/SIZE]

Sure. Now you run 1 OS instead of 2 at the same time. Have fun with it.

---

### Post by james.brantley on 2009-06-18
> **DeMus said:**
> Sure. Now you run 1 OS instead of 2 at the same time. Have fun with it.

[SIZE=3]Thanks for your assistance![/SIZE]

---


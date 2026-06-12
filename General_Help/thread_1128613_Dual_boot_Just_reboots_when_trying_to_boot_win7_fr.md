---
title: "Dual boot: Just reboots when trying to boot win7 from Grub"
date: 2009-04-17
forum: General Help
---

### Post by hallgeirl on 2009-04-17
Hi.

On my laptop I'm running Ubuntu (Jaunty RC) as the main OS. I have run WinXP as secondary (because I like games, eh :P), until now. I decided to switch WinXP for Windows 7. The problem is that when I try to boot Win7 from Grub, the system simply reboots. I get no error message or anything, it just reboots. Ubuntu works fine, and Win7 worked fine before I reinstalled Grub (which I had to do because Win7 was rude enough to overwrite my MBR).

Here is the output from fdisk -l (I have only one internal disk, sda):

```

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7d414ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1216     9767488+  83  Linux
/dev/sda2   *        1217        1242      204800    7  HPFS/NTFS
/dev/sda3            1242        3040    14445568    7  HPFS/NTFS
/dev/sda4            3041        7783    38098147+  83  Linux

```

And here is the relevant lines in /boot/grub/menu.lst:
```

title         Windows 7  
root          (hd0,1)
makeactive
chainloader   +1

```

Win7 is on /dev/sda2 and /dev/sda3. Supposedly, /dev/sda2 (the 200MB one) is the one I need to boot from, according to what I read around trying to figure this thing out.

So... anyone got any suggestions? :)

Thanks in advance for any advice.

---

### Post by meierfra. on 2009-04-17
In order to get a clearer picture of your setup, I suggest to boot into  Ubuntu  and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by hallgeirl on 2009-04-17
Hi!

Here is the RESULTS.txt from the boot info script.

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa7d414ba

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    19,535,039    19,534,977  83 Linux
/dev/sda2          19,535,872    19,945,471       409,600   7 HPFS/NTFS
/dev/sda3    *     19,945,472    48,836,607    28,891,136   7 HPFS/NTFS
/dev/sda4          48,837,600   125,033,894    76,196,295  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="d61e2729-b0ee-46f2-b668-30f758218190" TYPE="ext4" 
/dev/sda2: UUID="06CC8CD9CC8CC481" TYPE="ntfs" 
/dev/sda3: UUID="BA088C1A088BD3B3" TYPE="ntfs" 
/dev/sda4: UUID="e47b2cb2-569d-427f-ac5a-f7d7e1ab8d89" TYPE="ext2" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro)
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
/dev/sda4 on /home type ext2 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/hallgeir/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=hallgeir)


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
# kopt=root=UUID=d61e2729-b0ee-46f2-b668-30f758218190 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d61e2729-b0ee-46f2-b668-30f758218190

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
uuid		d61e2729-b0ee-46f2-b668-30f758218190
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d61e2729-b0ee-46f2-b668-30f758218190 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		d61e2729-b0ee-46f2-b668-30f758218190
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d61e2729-b0ee-46f2-b668-30f758218190 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		d61e2729-b0ee-46f2-b668-30f758218190
kernel		/boot/memtest86+.bin
quiet

title 		OSes that makes your brain melt:
root

title		Windows 7  
root		(hd0,1)
savedefault
makeactive
chainloader   +1

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
UUID=d61e2729-b0ee-46f2-b668-30f758218190 /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=e47b2cb2-569d-427f-ac5a-f7d7e1ab8d89 /home           ext2    relatime        0       2
/dev/sdb        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.3GB: boot/grub/menu.lst
   1.8GB: boot/grub/stage2
    .2GB: boot/initrd.img-2.6.28-11-generic
    .5GB: boot/vmlinuz-2.6.28-11-generic
    .2GB: initrd.img
    .5GB: vmlinuz

```

Cheers,
Hallgeir

---

### Post by codeseer on 2009-04-17
I may be wrong, but it's worth a try. I believe this:

```

title		Windows 7  
root		(hd0,1)
savedefault
makeactive
chainloader   +1

```

Should be this:

```

title		Windows 7  
root		(hd0,2)
savedefault
makeactive
chainloader   +1

```

---

### Post by hallgeirl on 2009-04-17
> **codeseer said:**
> I may be wrong, but it's worth a try. I believe this:

```

title		Windows 7  
root		(hd0,1)
savedefault
makeactive
chainloader   +1

```

Should be this:

```

title		Windows 7  
root		(hd0,2)
savedefault
makeactive
chainloader   +1

```

Hi,
I have tried this, and every other partition there is (hd0,0 to hd0,4 or so) with no luck. I get the exact same result.

I am quite sure that it's supposed to be (hd0,1), because, as I have understood it, it's on that 200MB partition that the boot loader for win7 is. 

Best regards,
Hallgeir

---

### Post by meierfra. on 2009-04-17
RESULTS.txt did not reveal any problems.

Couple of things to try:

Boot from the Win 7 CD. Choose "Repair Computer" and then "StartUp Repair"


If this did not cure your problem (and I actually doubt that it will):

Boot into Ubuntu and installing grub to the  boot sector of the Ubuntu partition:

```
sudo grub
root (hd0,0)
setup (hd0,0)
quit
```

Install a Window style MBR
```

sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```

Reboot and see whether you boot directly into Win 7.
(If this failed:  Boot from the Win 7 DVD, choose "Repair Computer" and then "Command Prompt". Type "bootrec /fixmbr" )

Once you booted into Win 7, use EasyBCD to add Ubuntu to the Win7 boot loader:

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)
(You can ignore the "Ubuntu Side of Things". Installing Grub the boot sector of the Ubuntu partition already took care of this part)

---

### Post by meierfra. on 2009-04-17
> I am quite sure that it's supposed to be (hd0,1)


Yes, it is.

> I have tried this, 

Did you try this after you run the boot info script?

If yes, set the boot flag back to the Win 7 boot partition before following the instructions from my previous post:

```
sudo sfdisk -A2 /dev/sda
```

---

### Post by codeseer on 2009-04-17
I don't get the 200 MB partition. That's a windows 7 thing?

---

### Post by meierfra. on 2009-04-17
> I don't get the 200 MB partition. That's a windows 7 thing?
Yes, it is.  Grub needs to chainload the partition which contains "bootmgr", which is /dev/sda2.

---

### Post by hallgeirl on 2009-04-17
Cheers guys.

meierfra, I tried changing the boot flag of the partitions both before and after I ran the boot info script. I'm now trying your method using the windows boot loader.

---

### Post by codeseer on 2009-04-17
> **meierfra. said:**
> Yes, it is.  Grub needs to chainload the partition which contains "bootmgr", which is /dev/sda2.

So, essentially they will be using either lilo or the windows boot loader to load grub?

---

### Post by hallgeirl on 2009-04-17
This is so incredibly strange...
I started up the win7 DVD, and chose "Repair". And sure enough, it found a problem with the boot manager. It said it fixed it, I rebooted... Chose Windows 7 in Grub, and I saw "Starting up...". It just hanged on "Starting up", so I rebooted. I chose windows 7 again, and poof, it rebooted and I was back to square 1.

I also tried to install lilo. Then I got a message that BOOTMGR was missing... I look a bit on the config of lilo, see if I can find something useful.

Edit: Forgot about doing the bootrec /fixmbr. I did that now, and now Windows boots up. So on to trying windows' boot loader.

---

### Post by meierfra. on 2009-04-17
> So, essentially they will be using either lilo or the windows boot loader to load grub? 

The "lilo" command essentially does the same thing as "fixmbr": Install some code in the MBR which just calls  the boot sector of the active partition.

So booting Ubuntu will work like this

MBR->boot sector of /dev/sda2 -> bootmgr(Windows boot loader)-> boot sector of /dev/sda1(Grub)


This looks like one of the rare case where grub is just not able to chain load Windows.

---

### Post by codeseer on 2009-04-17
> **meierfra. said:**
> The "lilo" command essentially does the same thing as "fixmbr": Install some code in the MBR which just calls  the boot sector of the active partition.

So booting Ubuntu will work like this

MBR->boot sector of /dev/sda2 -> bootmgr(Windows boot loader)-> boot sector of /dev/sda1(Grub)


This looks like one of the rare case where grub is just not able to chain load Windows.

Intentional, one might think?

Do you know the reason they gave for implementing a separate partition for boot in Win 7?

---

### Post by hallgeirl on 2009-04-17
Here's an update:
I managed to boot windows. I installed easyBCD, and I followed the instructions on the site you linked, adding a linux entry. I'm rebooting, I get the boot menu. I choose my Ubuntu entry, and I get an error:

"Windows failed to start. Blablabla
...
...
File: \NST\nst_grub-B8....7BC.mbr
Status: 0xc000000f
Info: The selected entry could not be loaded because the application is missing or corrupt."

I have tried reinstalling grub on /dev/sda1 after this with no effect. I also tried (just for the heck of it) to make a NeoGrub entry. That also fails with pretty much the same error message, just another .mbr-file.

EDIT: Update. I started ubuntu (yet again) and I mounted /dev/sda2 (where the win7 bootloader is hiding). It does seem that the .mbr-files did not get created for some reason. 

Any pointers? :)

---

### Post by meierfra. on 2009-04-17
Try this: set the boot_flag to the Ubuntu partition. (You should be able set boot flag with the Win 7 disk management)

Reboot and you should get the Grub menu.  See whether you can boot into Win 7 and/or Ubuntu from the Grub menu.

If you aren't able to boot into  both OSs, boot into Ubuntu  ( or the Ubuntu Live CD), run the boot info script and post the RESULTS.txt again. Make sure to post the new one, it might be called "RESULTS1.txt".

---

### Post by meierfra. on 2009-04-17
Maybe EasyBCD got confused by the Win7 boot partition. Anyway follow my advice from my last post.  A new RESULTS.txt should clear up the situation.

---

### Post by hallgeirl on 2009-04-18
Alright, I set the boot flag of my ubuntu partition. Here's what happend:
- GRUB showed up instead of the windows boot loader
- I chose "Windows 7" from the list, I got a "Starting up..." message, where it hung as last time.
- I rebooted, and the windows boot loader was back

I then tried to start Ubuntu again from the windows 7 bootloader, but with the same effect (I'm quite sure that the problem is that easyBCD doesn't create the .mbr-images (?) since those files clearly wasn't there when I mounted the 200MB partition).

Anyway, here's the latest RESULT.txt. Just ignore the /dev/sdb entries, that's my USB disk which I booted from, which is my old system disk:
```

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 218943 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa7d414ba

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    19,535,039    19,534,977  83 Linux
/dev/sda2    *     19,535,872    19,945,471       409,600   7 HPFS/NTFS
/dev/sda3          19,945,472    48,836,607    28,891,136   7 HPFS/NTFS
/dev/sda4          48,837,600   125,033,894    76,196,295  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbcdb4851

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    29,302,559    29,302,497  83 Linux
/dev/sdb2    *     29,302,560    48,837,599    19,535,040   7 HPFS/NTFS
/dev/sdb3          48,837,600    49,817,564       979,965  82 Linux swap / Solaris
/dev/sdb4          49,817,565   234,436,544   184,618,980  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="d61e2729-b0ee-46f2-b668-30f758218190" TYPE="ext4" 
/dev/sda2: UUID="06CC8CD9CC8CC481" TYPE="ntfs" 
/dev/sda3: UUID="BA088C1A088BD3B3" TYPE="ntfs" 
/dev/sda4: UUID="e47b2cb2-569d-427f-ac5a-f7d7e1ab8d89" TYPE="ext2" 
/dev/sdb1: UUID="8f5703c3-3fac-47f9-8d4e-0d15bd12a818" TYPE="ext4" 
/dev/sdb2: UUID="34109012108FD96E" TYPE="ntfs" 
/dev/sdb3: TYPE="swap" UUID="725ee885-0cbd-4c69-af98-25ee7ec7854d" 
/dev/sdb4: UUID="45b84525-99c9-4554-b614-9af2ceadd769" TYPE="ext4" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext4 (rw,relatime,errors=remount-ro)
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
/dev/sdb4 on /home type ext4 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/hallgeir/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=hallgeir)
/dev/sdb2 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


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
# kopt=root=UUID=d61e2729-b0ee-46f2-b668-30f758218190 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d61e2729-b0ee-46f2-b668-30f758218190

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
uuid		d61e2729-b0ee-46f2-b668-30f758218190
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d61e2729-b0ee-46f2-b668-30f758218190 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		d61e2729-b0ee-46f2-b668-30f758218190
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d61e2729-b0ee-46f2-b668-30f758218190 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		d61e2729-b0ee-46f2-b668-30f758218190
kernel		/boot/memtest86+.bin
quiet

title 		OSes that makes your brain melt:
root

title		Windows 7  
root		(hd0,1)
savedefault
makeactive
chainloader   +1

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
UUID=d61e2729-b0ee-46f2-b668-30f758218190 /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=e47b2cb2-569d-427f-ac5a-f7d7e1ab8d89 /home           ext2    relatime        0       2
/dev/sdb        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.3GB: boot/grub/menu.lst
    .1GB: boot/grub/stage2
    .2GB: boot/initrd.img-2.6.28-11-generic
    .5GB: boot/vmlinuz-2.6.28-11-generic
    .2GB: initrd.img
    .5GB: vmlinuz

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
# kopt=root=UUID=8f5703c3-3fac-47f9-8d4e-0d15bd12a818 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8f5703c3-3fac-47f9-8d4e-0d15bd12a818

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

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
uuid		8f5703c3-3fac-47f9-8d4e-0d15bd12a818
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8f5703c3-3fac-47f9-8d4e-0d15bd12a818 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic (recovery mode)
uuid		8f5703c3-3fac-47f9-8d4e-0d15bd12a818
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8f5703c3-3fac-47f9-8d4e-0d15bd12a818 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu jaunty (development branch), memtest86+
uuid		8f5703c3-3fac-47f9-8d4e-0d15bd12a818
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
rootnoverify	(hd0,1)
savedefault
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
# / was on /dev/sda1 during installation
UUID=8f5703c3-3fac-47f9-8d4e-0d15bd12a818 /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=45b84525-99c9-4554-b614-9af2ceadd769 /home           ext4    relatime        0       2
# swap was on /dev/sda3 during installation
UUID=725ee885-0cbd-4c69-af98-25ee7ec7854d none            swap    sw              0       0
/dev/sdb        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .6GB: boot/grub/menu.lst
   1.8GB: boot/grub/stage2
  10.7GB: boot/initrd.img-2.6.28-11-generic
   8.6GB: boot/vmlinuz-2.6.28-11-generic
  10.7GB: initrd.img
   8.6GB: vmlinuz

================================ sdb2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


```

I am now trying a full reinstall of both operating systems, installing windows first, then ubuntu.

Edit: I did this, and the same problem persists: Instant reboot...

Cheers, 
Hallgeir

---

### Post by codeseer on 2009-04-18
On a fresh install of both? Wow.

The results.txt is before the reinstall?

If this were a couple weeks later, after college turned out for the semester, I'd sacrifice my install to find a fix for you.

---

### Post by hallgeirl on 2009-04-18
> **codeseer said:**
> On a fresh install of both? Wow.

The results.txt is before the reinstall?


It is indeed.

> 
If this were a couple weeks later, after college turned out for the semester, I'd sacrifice my install to find a fix for you.

Hehe, the thought is appreciated :)

If any of you are running win7+Ubuntu, what build of win7 do you run? I'm running build 7000 of the beta, might there be a bug with older versions messing things up?

---

### Post by codeseer on 2009-04-18
I think it's a complication with the way Win 7 has that boot partition. Getting it to work around that is the issue though.

---

### Post by meierfra. on 2009-04-18
Yes, it looks like EasyBCD  did not create the .mbr files. So instead of using EsayBCD,  lets just edit the BCD with bcdedit.

I'm assuming that your setup has not changed (so Ubuntu is on /dev/sda1, the Win 7 boot partition on /dev/sda2, and Win 7 on /dev/sda3)


Step 1 Install Grub to the  boot sector of the Ubuntu partition:

Just as the last time.


Step 2 Copy the  boot sector to a file on the Win 7 boot partition:

```
sudo mount /dev/sda2 /mnt
sudo dd if=/dev/sda1 of=/mnt/Ubuntu.bin count=1
```
(be very careful with the "dd" command, if it runs for more than a couple  seconds, use "Ctrl+C" to stop the process.)


Step 3  Run "FixMBR" from the Win 7 DVD.

Just as before.


Step 4 Edit BCD

Boot into Win 7. 
Go to "Start". Type "cmd" and press "Ctrl+Shift+Enter". This will open a Win 7 commandline as an administrator. Type

```
bcdedit /create /d "Ubuntu" /application BOOTSECTOR
bcdedit /set {ID} device boot 
bcdedit /set {ID} PATH \Ubuntu.bin
bcdedit /displayorder {ID} /addlast 
bcdedit /timeout 5

```

Here ID is a very long number which  you will get after the first command. The braces need to be typed, too.
timout is the time in seconds before the default OS is started.

To minimize the amount of typing you need to do:

Copying:

Right-Click and select Mark.
Highlight text to be copied by dragging mouse over it.
Press "Enter"

Pasting: 

Right Click and select Paste (Previously copied text will be pasted to the command prompt)

You can also use the "UP arrow" to bring up the previously typed text.

---

### Post by hallgeirl on 2009-04-18
> **meierfra. said:**
> ...

You, sir, are a genious! The stuff in your last post worked PERFECTLY! :D

I can't thank you enough for all your help in this matter. It was first class. :)

---

### Post by meierfra. on 2009-04-18
> The stuff in your last post worked PERFECTLY!
I'm glad it worked, that was my last line of defense.

Have fun with Window 7 and Ubuntu.

---

### Post by codeseer on 2009-04-18
<Insert Kitchen Sink> :p

---

### Post by bendib on 2009-04-19
Darn it M$! Linux gives you an option! More anticompetitive behavior.

---

### Post by qwertymodo on 2009-04-19
Dang, that's just annoying.  I have Vista/7/Ubuntu Jaunty all installed with no problem and EasyBCD did the trick.  Sounds like you just had something funky goin on.

---


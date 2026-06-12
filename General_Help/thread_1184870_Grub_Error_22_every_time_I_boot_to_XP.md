---
title: "Grub Error 22 every time I boot to XP"
date: 2009-06-11
forum: General Help
---

### Post by kintarotpc on 2009-06-11
For some reason every time I boot into windows XP in my dual-boot setup, I hit a Grub error 22 when I reboot. Which means that I have to boot to an ubuntu live CD and reinstall grub (Grub, root (hd1,2), setup (hd0), quit, reboot) to get my boot loader back. 

I have dual booted in earlier setups including with vista and XP, but not using 9.04 (which is what I have been lately). As far as I know, XP shouldn't be rewriting my MBR on it's own, but that seems like that is exactly what it is doing. Any ideas on possible fixes for this?

---

### Post by coffeecat on 2009-06-11
> **kintarotpc said:**
> As far as I know, XP shouldn't be rewriting my MBR on it's own, but that seems like that is exactly what it is doing.

No, XP isn't rewriting the mbr, because if the mbr was rewritten, you'd lose grub stage 1 and then you wouldn't get any grub error message at all. From the grub manual for error 22:

> 22 : No such partition

This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk.Which is very curious. Post the terminal output of:

```
sudo fdisk -l
```and the contents of /boot/grub/menu.lst .

---

### Post by marsrover on 2009-06-11
whenever i got a error 22 it meaned mandriva goofed up
now i use ubuntu 
reinstall mandriva many times got error 22 every 5th boot

---

### Post by kintarotpc on 2009-06-11
Which is very curious. Post the terminal output of:

```
sudo fdisk -l
```and the contents of /boot/grub/menu.lst .[/quote]

 output of "Sudo fdisk -l"
```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0593fc5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14593   117218241   42  SFS

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e6a2e69

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4463    35841928+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2            4464        4587      996030   82  Linux swap / Solaris
Partition 2 does not end on cylinder boundary.
/dev/sdb3            4588        7297    21768075   83  Linux
Partition 3 does not end on cylinder boundary.

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x419a9251

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    7  HPFS/NTFS

```

And my menu.lst

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
# kopt=root=UUID=bb704af6-5323-4e0a-a181-71d714f34be4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=bb704af6-5323-4e0a-a181-71d714f34be4

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
uuid        bb704af6-5323-4e0a-a181-71d714f34be4
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=bb704af6-5323-4e0a-a181-71d714f34be4 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        bb704af6-5323-4e0a-a181-71d714f34be4
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=bb704af6-5323-4e0a-a181-71d714f34be4 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        bb704af6-5323-4e0a-a181-71d714f34be4
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
rootnoverify    (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

```

---

### Post by coffeecat on 2009-06-11
Tbh, I've never put Windows on sdb, so what I'm about to suggest may be wrong. I think the problem is in the map and rootnoverify commands. I believe you have to put the map commands first, and then rootnoverify will have to be (hd0,0), because you've remapped the first and second drives to each other, so your Windows stanza would be:

```
title        Microsoft Windows XP Professional
map            (hd0) (hd1)
map            (hd1) (hd0)
rootnoverify     (hd0,0)
makeactive
chainloader        +1
```There's a 'makeactive' in there for good measure, but this may not be necessary because your sdb1 is showing the boot flag as set.

What I don't understand is why you can boot into Windows first time, but not subsequently.

Sorry if this is off-beam but, as I said, I've managed to avoid putting Windows on anything but the first drive.

**Edit:** just had a quick look at some other threads, and I think I'm wrong about changing rootnoverify to (hd0,0). However, it seems that putting the root/rootnoverify command after the map commands is important.

Try:

 ```
title        Microsoft Windows XP Professional
 map            (hd0) (hd1)
 map            (hd1) (hd0)
 rootnoverify     (hd1,0)
 makeactive
 chainloader        +1
```

---

### Post by Entropy_Sam on 2009-06-11
Coffeecat - good guess and it might even work, but IME it's not necessary to do it that way.

I was wondering about throwing in a **makeactive** but I don't really see what difference that would make, either.

kintarotpc - Take a careful look at the way menu.lst looks now, then when you reboot after goign into XP, see if it's changed at GRUB startup. Also, take a look at your hard drives as GRUB sees them after rebootign from XP and see if they are in anotehr order for some reason (I had similar troubles with BIOS reordering drives occasinoally, especially if I boot with a USB flash drive connected).

---

### Post by Entropy_Sam on 2009-06-11
You can take a look at your hard disk order as seen by GRUB by going to the GRUB command prompt, typing **root(** and using tab autocomplete to display your options then you can try **root(0,** and tab autocomplete to see which partitions are available (0x7 is NTFS, 0x83 is Linux and 0x82 is Linux Swap iirc).

---

### Post by muad on 2009-06-11
> **Entropy_Sam said:**
> 
I was wondering about throwing in a **makeactive** but I don't really see what difference that would make, either.

If I take **makeactive** out on my menu.lst for XP, it will not boot.

Also, go into your BIOS and be sure that 250GB drive is On.

---

### Post by muad on 2009-06-11
Which drive you are trying to boot windows off of? /dev/sdb or /dev/sdc???

If /dev/sdc, try this in your menu.lst

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional  
rootnoverify        (hd2,0)
savedefault
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1

```

Thanks to Sam's help, I was just able to get my working, and I originally got the Same Error 22.

---

### Post by kintarotpc on 2009-06-11
So far no good on the suggestions so far. Perhaps I should be a little more clear , maybe, in case I haven't been so far. The issue is that I get this grub error only after booting into XP. This means that I can reboot into linux over and over no problem, but as soon as I boot into  XP, bam - error.

And to answer Muad's answer, XP is installed on sdb1.

Oh yes, and when setting up grub I've been setting the root to hd1,2 and setting it up (setup command) to hd0. If this is wrong, let me know, because no other settings seem to work at all.

---

### Post by merlinus on 2009-06-12
This info concerns me:

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e6a2e69

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4463    35841928+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2            4464        4587      996030   82  Linux swap / Solaris
Partition 2 does not end on cylinder boundary.
/dev/sdb3            4588        7297    21768075   83  Linux

It would seem that there are definitely partition errors.
Partition 3 does not end on cylinder boundary.

---

### Post by kintarotpc on 2009-06-12
> This info concerns me:

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e6a2e69

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4463    35841928+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2            4464        4587      996030   82  Linux swap / Solaris
Partition 2 does not end on cylinder boundary.
/dev/sdb3            4588        7297    21768075   83  Linux

It would seem that there are definitely partition errors.
Partition 3 does not end on cylinder boundary.

That is rather disconcerting, now that you point that out. I suppose I shouldn't be terribly surprised that there are disk errors like this. sdb is my oldest drive, dating back at least seven years and it's been through a lot. Might be time to just replace the drive. Even if these errors are repairable by software, it could use the replacement if only for the speed of sata.

---

### Post by adam_kimber on 2009-06-12
If you are going to repartition and reinstall things. I would always recommend keeping windows on the primary interface (0,0) and linxu can go on any other. I would also recommend have a seperate partition for /home as this would help protect your personal data. (it also makes a reinstall far easier).

---

### Post by coffeecat on 2009-06-12
> **adam_kimber said:**
> I would always recommend keeping windows on the primary interface (0,0) and linxu can go on any other.

**kintarotpc**, I agree with keeping Windows on the "master" drive - (hd0). It means you avoid those confusing map commands in grub. Also don't forget that although Windows needs to boot from a primary partition, Linux has no such limitation. I noticed that your Ubuntu root and swap partitions are on primaries. What I like to do is to create an extended partition for all my Linux partitions. This is what I've done on all my machines - one extended partition containing a number of logical partitions for a multiboot setup, with one shared swap partition. Even if you don't intend to multiboot, using extended/logical partitions gives you more flexibility. You'll find a lot of threads where people have backed themselves into a corner by using up the maximum of only four primary partitions.

---

### Post by merlinus on 2009-06-12
+ 10 to both of these suggestions!

---


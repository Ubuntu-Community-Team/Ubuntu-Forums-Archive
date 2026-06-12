---
title: "At my wit's end with GRUB"
date: 2009-06-17
forum: General Help
---

### Post by Fleshtone on 2009-06-17
Hello all,

I'm dual booting Jaunty and Windows XP pro SP3, and while trying to get the GRUB menu to work properly (it wasn't loading windows and got Error 22 when I had my USB drives plugged in), I made it stop working altogether.

The only way to get anything running is by booting to Super Grub Disk, selecting "Boot Partition on Gnu/Linux", and choosing the partition with Jaunty on it, in my case SDB(HD1,4), which then brings up a GRUB menu from which everything (including Windows) works.

Just about nothing else in SGD works, including:

-Automatically install grub (error 15: file not found Booting 'not lucky')

-Boot gnu/linux directly (find /etc/fstab error 15:file not found)

-Fix boot of gnu/linux (select file /grub/stage1 /boot/grub/stage1 error 15: file not found booting 'not lucky')

Windows is here:  SDA (HD0)
Jaunty is here:   SDB (HD1,4)  <--it's on a partition on that drive so I'm not sure I am writing it right.

In Super Grub Disk, I noticed that on SDB there is a windows partition (HD1,0) which may be causing problems.  

My BIOS boot order is:
1:Floppy
2:CD
3:HD0 (Windows)
4:HD1 (with Jaunty)

I've changed the order many times and the current order is the only one that works even slightly.

I know there is a lot of help up here about GRUB, but I've had a tough time adapting that info to my situation, indeed I have made my situation worse.

I reinstalled GRUB from the package manager, which did nothing.  I looked over menu.lst, but I'm not totally sure what it should look like.  

Any advice here would be very appreciated!

---

### Post by merlinus on 2009-06-17
Post

```

cat /boot/grub/menu.lst
sudo fdisk -l

```

---

### Post by Fleshtone on 2009-06-17
output of ```
cat /boot/grub/menu.lst

```
> 
fleshtone@ubuntu-desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=74f1fb05-d8fd-40b8-9163-7e5c6439b2a1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=74f1fb05-d8fd-40b8-9163-7e5c6439b2a1

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
uuid		74f1fb05-d8fd-40b8-9163-7e5c6439b2a1
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=74f1fb05-d8fd-40b8-9163-7e5c6439b2a1 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		74f1fb05-d8fd-40b8-9163-7e5c6439b2a1
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=74f1fb05-d8fd-40b8-9163-7e5c6439b2a1 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		74f1fb05-d8fd-40b8-9163-7e5c6439b2a1
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
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows NT/2000/XP
rootnoverify	(hd0,1)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


Output of ```
sudo fdisk -l
```
> 
Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4382    35198383+   7  HPFS/NTFS

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf77ba720

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1459    11719386    7  HPFS/NTFS
/dev/sdb2            1460        4998    28427017+   f  W95 Ext'd (LBA)
/dev/sdb5            1460        4998    28426986   83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b5566e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641    7  HPFS/NTFS


---

### Post by merlinus on 2009-06-17
If you look at the end of menu.lst, you will see two different entries for windows.  So, which hdd and partition is it on?  You have ntfs partitions on all three hdds.

Also, what is the booting order of your hdds in bios?

---

### Post by Fleshtone on 2009-06-17
The BIOS boot order is:
1:Floppy
2:CD
3:HD0 (Windows)
4:HD1 (with Jaunty)

As for the two windows entries, I believe one is for the Windows recovery console.  They are both on /dev/sda(HD0).

One thing that looks strange on the fdisk -l output is that the /dev/sdc drive is listed as bootable, but it does not carry an OS.  Additionally, the ext25fs partition on /dev/sdb2, which carries Jaunty, is NOT denoted as bootable, which it should be if I'm not mistaken.

I'm not sure why I partitioned /sdb instead of just giving it over to Jaunty completely.  That might have simplified things.

---

### Post by SirrKitt on 2009-06-17
Well, I BELIEVE that you don't need the second windows entry in that.
Even if you have a recovery console, that's managed all by Windows' boot manager. So, I'm thinking you should delete the second windows entry.
I'll scan over the stuff a little more and see if I can find any  other errors, so far, it seems like you just have some little typos and stuff.

```

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root
```
I don't think that that root should be there. Erase that.

Do you know what hard drive or partition(s) (according to Linux) your windows is installed on? I'm not sure, since I see a couple of NTFS, and etc. stuff. 

From what I see, I think you should use this for Windows.
You might try (hd2,0) for that rootnoverify, too.
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

```


And I think this MIGHT do it for Ubuntu.
```

title Ubuntu 9.04, kernel 2.6.28-11-generic
root (hd1,4)
kernel /boot/vmlinuz-2.6.28-11-generic ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic
quiet

```
I'm not POSITIVE about the partition numbering. Been a while since I screwed with Grub.
 
If this doesn't work, you might be able to use QGrubEditor or KGrubeditor. Just search GRUB in Synaptic and download one of those GUIs. They oughta detect Windows and the such and then add it into your grub.conf

Would you be able to run gparted and take a few screenshots?
Not sure if that'd help, but it couldn't help.
You might have some partitions screwed up.

So, for a copy + paste thing you can TRY
```


default 0

timeout 10


### BEGIN AUTOMAGIC KERNELS LIST
title Ubuntu 9.04, kernel 2.6.28-11-generic
root (hd1,4)
kernel /boot/vmlinuz-2.6.28-11-generic  ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic
quiet

title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root (hd1,4)
kernel /boot/vmlinuz-2.6.28-11-generic ro single
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, memtest86+
root (hd1,4)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:

title Microsoft Windows XP Professional
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

```

---

### Post by merlinus on 2009-06-18
ubuntu root = (hd1,4)

---

### Post by SirrKitt on 2009-06-18
Are yeh positive about that?
Hmm... I'm bad at counting partitions for GRUB, I prefer just guess and reboot and if it boots, it's right. >__<
Does Ubuntu put /boot into its own ext2 partition by default?
It seems like it does.
Hmm...
But (Hd1,4) makes since.
Now I wonder which NTFS partition he uses as the Winz root.
<__<

---

### Post by merlinus on 2009-06-18
@fleshtone

> 
As for the two windows entries, I believe one is for the Windows recovery console.  They are both on /dev/sda(HD0).


sudo fdisk -l only shows one ntfs partition on sda.

@sirrkitt

Numbering for these things begins at 0 (zero).  Linux is on sdb5, which translates to (hd1,4).

---

### Post by Fleshtone on 2009-06-18
Ok, I tried making some of the small changes to menu.lst, such as removing that "root" and the second Windows entry.  Those changes did not help or hinder my cause.

Then I tried just pasting that whole section that SirrKitt said to TRY, and you were right to emphasize "try", because it made to whole thing unbootable, so I had to run the live CD to revert menu.lst.  I knew that was a shot in the dark, but I figured what the hey.

After more poking around in Super Grub Disk, it seems like the problem with the menu.lst and grub.conf files is not their contents so much as their *location*.  SGD can't find any of those files.  But when I boot a partition, then pick the sdb5 partition, it obviously finds those files because it brings up the GRUB menu.  

I think I need to point at sbd5 as the starting point for starting up, but I am not sure how.  There is a good chance that I've made a mess of all this by trying too many options in SGD, and activating or deactivating things errantly.  At one point I really confused myself after "swapping" disks that shouldn't have been swapped.

Also, I installed kgrubeditor, but when I try to run it, it doesn't come up.  It just says "starting kgrubeditor" for a few seconds, then closes.

---

### Post by Fleshtone on 2009-06-18
I followed these [directions]("http://ubuntuforums.org/showthread.php?t=224351") and reinstalled GRUB.  This seems to have worked for the most part.  Powering on brings up the GRUB menu, and the menu can then launch Jaunty.

The GRUB menu, however, can not start Windows.  I've tried many variations in menu.lst to locate Windows.  I believe it should be (hd0,0), but that returns "Error 13: invalid or unsupported executable format"

(hd0,1) returns error 22: no such partition.

---

### Post by merlinus on 2009-06-18
Can you boot windows at all, using supergrub or your original cd?

Also, please repost the last parts of menu.lst, since as you said you have made a number of changes and such.

---

### Post by Fleshtone on 2009-06-18
Ugg!  I ran Super Grub Disk and let it "Fix Boot of Windows", and now everything is re-broken.  SGD can not boot windows, but it can boot Jaunty using the same Boot Partition method I was using earlier.

If I let the system power up without the SGD disk present, the monitor just flashes black and brighter black.  Also, since this problem started yesterday, the CPU fan is running very high, if that means anything.

I am going to reinstall GRUB again and try to get back to the somewhat less pressing problem of not being able to boot windows.

This is the current menu.lst.  Windows' (hd0,0) returns "error 13: invalid or unsupported executable format".

> title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		74f1fb05-d8fd-40b8-9163-7e5c6439b2a1
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=74f1fb05-d8fd-40b8-9163-7e5c6439b2a1 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		74f1fb05-d8fd-40b8-9163-7e5c6439b2a1
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=74f1fb05-d8fd-40b8-9163-7e5c6439b2a1 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		74f1fb05-d8fd-40b8-9163-7e5c6439b2a1
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Geffers on 2009-06-18
> **Fleshtone said:**
> Hello all,

I'm dual booting Jaunty and Windows XP pro SP3, and while trying to get the GRUB menu to work properly (it wasn't loading windows and got Error 22 when I had my USB drives plugged in), I made it stop working altogether.

Any advice here would be very appreciated!

The following link is an excellent GRUB explanation, I have a separate GRUB partition that chainloads to various OSs with their own GRUB installed.

[http://members.iinet.net.au/%7Eherman546/p15.html#root](http://members.iinet.net.au/%7Eherman546/p15.html#root)

Geffers

---

### Post by Fleshtone on 2009-06-18
Thanks very much for that resource on GRUB, and thanks to everyone for your help so far!  I reinstalled GRUB and I'm back to the folowing state:

-GRUB menu loads.

-Jaunty will launch from GRUB menu.

-Windows will not launch from GRUB menu (Error 13)

-Windows will not launch by any other means, such as going to BIOS and specifying which drive to boot from, which I believe should bypass GRUB.  When I do this, the system enters a loop, attempting to boot IBM's recovery utility and then restarting ad infinitum.

I've read through that GRUB info and some of the linked pages, but I'm still scratching my head.

It comes down to this output indicating that /dev/sda is indeed (hd0)...
> fleshtone@ubuntu-desktop:~$ cat /boot/grub/device.map
(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc


...and menu.lst containing this entry...
> title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive

chainloader	+1

...and Windows still not loading, and returning "error 13: invalid or unsupported executable format".

GRUB boots fine and successfully starts Jaunty but that sad truth is I still need Windows.  It seems like any time I try to use Super Grub Disk to fix this, it breaks it further.

---

### Post by Fleshtone on 2009-06-19
I wonder what's this business with "map (hd0) (hd1) / map (hd1) (hd0)" on the second Windows entry.  The GRUB documentation I read does mention this, but it doesn't actually define what is happening.  Is there a chance that I need to add some map tags to the primary windows entry?


> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Windows NT/2000/XP
rootnoverify (hd0,1)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 

---

### Post by merlinus on 2009-06-19
If windows is on your second hdd (or third or fourth, etc.), then map statements are needed.  IIRC, yours is on the first partition on the first hdd, so no map statement is needed.

---

### Post by Fleshtone on 2009-06-22
I still can't figure this out. Windows does not boot at all.  When I run Super Grub Disk it has an option to automatically "fix" GRUB.  But it returns the error "/boot/grub/stage1 file not found"

This seems strange because GRUB can successfully boot Jaunty, which I imagine would require stage1.  Is there more than one stage1?

---

### Post by merlinus on 2009-06-22
At this point, it seems your only viable option is to restore xp to the mbr using its cd.  Then you can reinstall grub.  It may be possible to do this using supergrub.

---


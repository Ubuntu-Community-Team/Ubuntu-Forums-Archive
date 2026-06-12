---
title: "Doesn't boot XP or FF 7-04 raid0 - completely stuck"
date: 2007-06-02
forum: Dell  Ubuntu Support
---

### Post by plo on 2007-06-02
Hi!

Tried to find solution in various forum but none of the suggestions seems to work for me.
I'm able to boot the live CD Feaisty Fawn 7.04 but I'm not able to fix Grub.
If I enter grub and look for /boot/grub/stage1 it cant find the file
If I boot windows CD it can't find any discs.
In bios the drives are set as Intel array - raid 0 and that seems OK.

My system is:
-- Dell 8400 with raid0 discs of 160 Gb each (bios says Intel array).
- Windows XP SP2 with 3 partitions C,D och E (+ someth:(ing called Dell utility).
- Removed data from partition E and installed DesktopUbuntu Feisty Fawn 7.04 (did not create any extra partitions for /swap ..).
- Did not enter advanced mode for install (maybe big mistake)
- Installation was OK but ...
- At startup I get GRUB error 21
- If I boot from Live CD and type fdisk -l (as root) i get

[I]root@ubuntu:~# fdisk -l
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0xffffb078 of partition table 5 will be
corrected by w(rite)

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2   *           9        3960    31744440    7  HPFS/NTFS
/dev/sda3           38546       38904     2883667+  db  CP/M / CTOS /
...
/dev/sda4            3961       38545   277804012+   f  W95 Ext'd
(LBA)
/dev/sda5   ?       90530       86496  2115078273   de  Dell Utility

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table[/I]

If I run the Ubuntu partition manager it shows sda and sdb but no partitions.

Please help :(

/Palle

---

### Post by bapoumba on 2007-06-03
Thread moved to "Ubuntu Dell Support" sub forum.

---

### Post by CCIEMD on 2007-06-03
Hi,

It sounds like your setup came configured under Windows using RAID configured in the BIOS.  Most current chipsets (including Intel, Nvidia, AMD, etc.) include a RAID feature.  Unfortunately, these RAID setups still require software to do most of the work and don't actually do the RAID processing in hardware.

This is commonly referred to as "fakeraid" in Linux.  Ubuntu does not recognize these "fakeraid" partitions by default.  Unfortunately, you probably hosed the Windows partitions when you tried to do your Ubuntu install.  

If you want Ubuntu to recognize a RAID 0 setup, you have to use a package called DMRAID.  Take a look at the URL below for more info:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

This is currently somewhat of a hassle.  It is generally recommended that if possible to us the Linux software RAID instead (the package is called MD and it should be installed by default).

To get Windows working again, you will need to load the Intel RAID drivers from a disk when booting from the Windows CD.

Hope this helps.

Richard

---

### Post by bettyhills on 2007-06-03
That FakeRaidHowto is daunting.  

I, too, purchased the E520 - similar system specs - and spent two days trying to install until _succeeding_.  U-FF does not recognize the RAID drive.   I am in the process right now of reinstalling U-FF 7.04 i386 to fine tune my partitions, and while doing so will write out steps for the process.  

The trick was to pre-partition the entire drive as it needed to be for U-FF, and then install MANUAL method selecting those prepared partitions.  It went in smooth as silk using U-FF i386.  I used Partition Magic 8.0 for the prep work ($19 on eBay genuine retail box).

If your Windows installation is intact, use a partitioning program to prepare your drive, and then install away.

---

### Post by plo on 2007-06-04
CCIEMD: Thank's, I was abit puzzled when the raid was OK in bios but wouldn't boot. I did'nt know I needed software drives for the raid to work properly in windows. I will try when I get back home tomorrow and hopefully I'll be able to restore my windows config.
I've looked at the Fakeraid setup and I agree, not an easy newbee setup.
My other option is a spare harddrive I have. If there's room I'll install that and use it for Ubuntu instead.

bettyhills:Are you also doing dual boot?  If so your notes might be helpful to me. 


Thank's again

---

### Post by igloocentral on 2007-06-04
you can actually install ub ff to a dell raid using the live cd, with just a little extra effort. i have done it on my dell poweredge 420. i will write it up soon but until then...

run the live cd and install dmraid using synaptic
startup the installer and pretend you are installing to the first drive showing ( the base raid volume )
-make sure you mark all other partitions as do not use including any other swap partitions it finds!
continue with the installer until it gives you a big bad error message
run dmraid -ay a bunch of times in the background, the partitions should show up
-OTHERWISE DON'T CONTINUE
go back into the installer to the "prepare partitions" screen and look for your raid partitions
-you should be able to set the installer to setup on your raid partitions and then continue
the installer should then go and do the whole install except GRUB !
go back to a shell and mount your sysfs file system and chroot /target
copy the stage1 etc files as outlined in the fakeraidhowto and fakeraidedgy
configure your menu.lst file and run grub to set up the MBR as outlined in the fakeraidhowto
your fstab file will have already been setup by the gui installer!

i'll write a better howto soon. if you partition your raid before starting, you can skip steps 2, 3, 4 !

---

### Post by plo on 2007-06-06
Problem solved (or at least partially).
Raid drivers fixed so XP CD did boot. However I never succeded to fix MBR via recovery console.
I did not have the Admin password (yes I tried with just ENTER), which is weird because I did not set any when I installed windows in the first place.

I installed an extra drive and loaded XP on that so I could boot and access all files on the raid discs.
Now I will disable raid and install XP on one and Ubuntu on the other and then use the third disk to share data.

Thanks for the help.

Note: I've seen a lot of threads by people having problems with dual boot and grub. A guide describing different drive configurations and install methods would probably be very helpful. Or at least give some warnings about configurations that are more difficult to get to work properly. Great work with the guides otherwise.

/ Palle

---


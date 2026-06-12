---
title: "BIG boot problem (grub)"
date: 2005-11-08
forum: Desktop Environments
---

### Post by Greyfoxwolf on 2005-11-08
AMD-64 3000+
mobo: Asus a8n-sli
drives: 1 ide master 120 GB drive
 1 2nd ide master dvd-recorder
1 sata 200GB drive
!!NO DISK DRIVE (i know, its stupid...)!!


i had to install windows (on the ide drive) because of poor game support on p2p and cedega
so i backed up most stuff knowing that windows would whipe uvrythang.
Well it did, but it destroyed my MBR too (i think). now i cannot boot windows without the installation cd (win xp sp2 09-11 mm-dd custom build). if i remove the installation cd my mobo moans about loading a bootable disk...
this is after installing windows (and even booting into it, very very strange)

so i thought, well installing kubuntu (on the ide drive) would solve the problem, all datat was installed succesfully BUT grub, i tried virtualy EVERY thing to get grub installed (using difrent partitions, deleting partitions and remaking them, setting bootable flags on and off, "restore grub with install cd" method) grub just wont install, it just gets stuck @ 0% and lilo gets stuck @ 50% and NO the disc is not corrupt because i installed breezy several times with this disk.

if its nececary i can go to a friend and download a live cd of any distro.

EDIT: i also checked my bios settings for boot, if any help
First boot: cdrom
Second: harddisk
Third: harddisk
fourth: harddisk

---

### Post by Greyfoxwolf on 2005-11-09
no body? 
im stuck in windows, its a frigin torture. i realy dont know how to solve this problem. any help would be realy apreciated

---

### Post by Greyfoxwolf on 2005-11-09
well tnx for all the help. seems i will have to do a low level format...........

---

### Post by metoo on 2005-11-11
Your IDE Drive will be /dev/hda and your SATA drive /dev/sda in Linux. (/dev/hdb the DVD-writer)

The question is where did you install grub onto? I cannot tell you in which order linux 'sees' your drives.
My guess would be (hd0,0) is the IDE. But that's just a guess.

However, your boot order:
Can you define the boot hd in more detail in the BIOS? Then you could just test the entries.
Further, there might be other settings for the SATA part (like RAID or not...) which might define, whether to boot from SATA or IDE first. Take a look into the BIOS...

I don't have a nvidia chip set, so I cannot help more.

I doubt that any kind of low-level formating will help, if you can enable it at all. These days you hardly do anything like that anymore.

---

### Post by vitorsouza on 2005-11-11
I only know the basics, so it may be of no help what I'm about to say. Anyways, when my grub stops working I use Kubuntu's install CD, since the notebook doesn't have a floppy drive. What I do is type "rescue" on the CD boot screen and it displays a limited console, from which I run grub and issue commands.

To restore my grub installation, I do this:

root (hd0,1)
setup(hd0)

It works because (hd0,1) is where Kubuntu is installed and grub is located in its default dir: /boot/grub. This way, setup (hd0) installs grub back in the MBR of the first HD. Otherwise, the command is much more complex. Also, /boot/grub/menu.lst has to be properly configured, but Kubuntu did that for me...

If you don't know which HD has grub installed, you can use the command:

find /boot/grub/stage1

It displays all (hdX,Y) that have that file present in the file system.

Again, this is all basic stuff, but I wanted to say it because I don't know what you have or have not tried yet. Hope it helps.

V&#237;tor Souza

---

### Post by Greyfoxwolf on 2005-11-11
well, i cant set the boot order of the drives
in the bios it says that the first boot device is my sata hdd anyway the problem is it cant be placed in ANY of them AND even windows "uber" "everything-is-automated" crap cant make any of the hdd bootable :)
like i said, somthing has happened to my mbr afte windows whiped the entire disk, its like non-existant.
im still searching for a solution will give it about a week, if it isnt solved by then, ill backup this windows partition, do a lowlevel format, install windows, restore the backed up partition, instal kubuntu and thereby install grub to dualboot. 
any help is welcome

btw: ther is no hdX0, bootloader or whatsoever, thats the problem, its all partioned disk space, like i said i tried recovering grub ("all" the know ways in this forum), did fixmbr and fixboot (windows recovery commands). they all failed

---

### Post by rune on 2005-11-11
Have you tried making a grub boot disk? and then running grub from that booting linux? I had problems with grub due to faulty bios geometry setup.

---

### Post by Greyfoxwolf on 2005-11-12
LOL
i thought of that, i was gonna buy a disk drive today anyway. this should be fun
, it isnt the best solution but i am not complaining. 1 mb should be enough to hold windows boot and grub i suppose, now i just need to know how to build a floppy that would fire up the windows in my hdd :)

---

### Post by metoo on 2005-11-12
You don't see the bootloader in fdisk.

Grab a live CD (via Windows), take the IDE HD out, so you know, that your one and only HD is /dev/sda .
Then ( from the live CD) use
cfdisk /dev/sda
and see if cfdisk works fine with your drive.

If it does, try to install Grub via the live CD. The forum or Wiki should hold a guide, I just don't know how.

Refering to the previous post:
when in the live CD:
- open a terminal
- grub + enter
- root (hd0,0) + enter					for root ( '/') auf sda1 (the 1st partition, if no extra /boot partition, else add up: hd0,1 or hd0,2 . You know the partitions from the cfdisk test)
- setup (hd0) + enter					for mbr auf sda
- quit + enter
- re-boot

might be worth a try.

---


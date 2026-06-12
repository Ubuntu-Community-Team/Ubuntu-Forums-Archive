---
title: "No CD Rom on my new Ubuntu install"
date: 2004-12-04
forum: Desktop Environments
---

### Post by frspin on 2004-12-04
I have installed Ubuntu from my RH9 running system, according to 
"Installing Ubuntu from a Unix/Linux System

All was correct and now I have a working Ubuntu but:

- no /media/floppy0 and /media/cdrom0 directory
- no mount of floppy or CD when I insert it

My /etc/fstab say:

/dev/hdc  /media/cdrom0  udf,iso9660 ro,user,noauto 0 0
/dev/fd0  /media/floppy0   auto             rw,user,noauto 0 0

If I mount using Nautilus->Computer->Floppy or CD I get an error message
with a "nonexistend directory"

I have created /media/cdrom0 and /media/floppy0.
No auto mount at all.
Mounting with Nautilus a floppy I get an error:

mount: I could not determine the filesystem type, and none was specified

Add, if I put vfat as system type in /etc/fstab I get correct nautilus-made mount

For CD instead I still get no automount and, using nautilus, this message:

mount: special device /dev/hdc does not exist

In /dev there is no hdc entry but in /var/messages there is a hdc device. This my /var/messages file:

Dec  4 14:16:38 franco kernel:     ide0: BM-DMA at 0xdc00-0xdc07, BIOS settings: hda:DMA, hdb:DMA
Dec  4 14:16:38 franco kernel:     ide1: BM-DMA at 0xdc08-0xdc0f, BIOS settings: hdc:DMA, hdd:pio
Dec  4 14:16:38 franco kernel: hda: WDC WD400BB-00DEA0, ATA DISK drive
Dec  4 14:16:38 franco kernel: hdb: Maxtor 6Y060L0, ATA DISK drive
Dec  4 14:16:38 franco kernel: Using anticipatory io scheduler
Dec  4 14:16:38 franco kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Dec  4 14:16:38 franco kernel: hda: max request size: 128KiB
Dec  4 14:16:38 franco kernel: hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
Dec  4 14:16:38 franco kernel:  /dev/ide/host0/bus0/target0/lun0: p1 p2 p3
Dec  4 14:16:38 franco kernel: hdb: max request size: 128KiB
Dec  4 14:16:38 franco kernel: hdb: 120103200 sectors (61492 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)
Dec  4 14:16:38 franco kernel:  /dev/ide/host0/bus0/target1/lun0: p1 p2 p3
Dec  4 14:16:38 franco kernel: hdc: CRD-8482B, ATAPI CD/DVD-ROM drive
Dec  4 14:16:38 franco kernel: ide1 at 0x170-0x177,0x376 on irq 15
D


So, I am missing some daemon or other software for making a /dev entry or I have to make this by hand ? And, if so, how can I made it?

Regards

Franco Spinelli

---

### Post by bob k on 2004-12-04
[QUOTE=frspin]I have installed Ubuntu from my RH9 running system, according to 
"Installing Ubuntu from a Unix/Linux System

All was correct and now I have a working Ubuntu but:

- no /media/floppy0 and /media/cdrom0 directory
- no mount of floppy or CD when I insert it

My /etc/fstab say:

/dev/hdc  /media/cdrom0  udf,iso9660 ro,user,noauto 0 0
/dev/fd0  /media/floppy0   auto             rw,user,noauto 0 0

If I mount using Nautilus->Computer->Floppy or CD I get an error message
with a "nonexistend directory"

I have created /media/cdrom0 and /media/floppy0.
No auto mount at all.
Mounting with Nautilus a floppy I get an error:

mount: I could not determine the filesystem type, and none was specified

Add, if I put vfat as system type in /etc/fstab I get correct nautilus-made mount

For CD instead I still get no automount and, using nautilus, this message:

mount: special device /dev/hdc does not exist

In /dev there is no hdc entry but in /var/messages there is a hdc device. This my /var/messages file:

Dec  4 14:16:38 franco kernel:     ide0: BM-DMA at 0xdc00-0xdc07, BIOS settings: hda:DMA, hdb:DMA
Dec  4 14:16:38 franco kernel:     ide1: BM-DMA at 0xdc08-0xdc0f, BIOS settings: hdc:DMA, hdd:pio
Dec  4 14:16:38 franco kernel: hda: WDC WD400BB-00DEA0, ATA DISK drive
Dec  4 14:16:38 franco kernel: hdb: Maxtor 6Y060L0, ATA DISK drive
Dec  4 14:16:38 franco kernel: Using anticipatory io scheduler
Dec  4 14:16:38 franco kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Dec  4 14:16:38 franco kernel: hda: max request size: 128KiB
Dec  4 14:16:38 franco kernel: hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
Dec  4 14:16:38 franco kernel:  /dev/ide/host0/bus0/target0/lun0: p1 p2 p3
Dec  4 14:16:38 franco kernel: hdb: max request size: 128KiB
Dec  4 14:16:38 franco kernel: hdb: 120103200 sectors (61492 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)
Dec  4 14:16:38 franco kernel:  /dev/ide/host0/bus0/target1/lun0: p1 p2 p3
Dec  4 14:16:38 franco kernel: hdc: CRD-8482B, ATAPI CD/DVD-ROM drive
Dec  4 14:16:38 franco kernel: ide1 at 0x170-0x177,0x376 on irq 15
D


So, I am missing some daemon or other software for making a /dev entry or I have to make this by hand ? And, if so, how can I made it?

Regards

Franco Spinelli[/QUOTE]
 I've run into some of this before, they use symbolic links for the removable drives, but I have a /media entry for my cdrom0 and floppy0 and a symbolic link for cdrom and floppy. I cannot address the /media/cdrom0 & floppy0, but I can address these drives by there symbolic link (ie cdrom & floppy) and thats the way I have to talk to them in apps like XMMS & CD-player.... also if you have a CD rw DVD rom you will have to make a symbolic link something like this  $sudo ln -sf /media/cdrom0 /dev/dvd. I haven't put this in a config file yet but it has to be done every time you restart. I just alaised the commands in my local .bashrc file untill I have a better handle on whats going on at that level.

I have'nt had time to figure out the little stuff with getting a new distro running some what up to par but I'm close and i'll have a little more time to dig around and figure why they did it this way.

Bob

---

### Post by Marauder1 on 2004-12-05
You sure you were root when you created those directories ?
My fstab is the same as yours and everything is ok !!!

---

### Post by frspin on 2004-12-07
My problem is that I dont have a /dev/hdc entry.
I think that udev have to create a /dev/hdc entry when I insert a CD or at boot time.
In /dev I have entries for my disks, for my audio devices, for my input devices and also for my floppy device but no entry for my cdrom (as /dev/cdrom or as /dev/hdc)

Regards

Franco Spinelli

---

### Post by frspin on 2004-12-07
I have put ide-cd module (not automatically loaded at boot time) in /etc/modules and now I have a /dev/hdc and a /dev/cdrom entry.
I can play manually audio cd and, after making /media/cdrom0 entry, I can mount it using Nautilus.
Still missing any automation. When I insert an audio CD gnome-cd is not starting and inserting a data CD there is no auto mount and no auto browse.

Obviously, preferences for removable devices are checked

Regards
Franco Spinelli

---

### Post by kamstrup on 2004-12-09
It sounds a bit like HAL isn't running to me... What does "ps -C hald" say?

---

### Post by frspin on 2004-12-09
[QUOTE=kamstrup]It sounds a bit like HAL isn't running to me... What does "ps -C hald" say?[/QUOTE]

Output from "ps -C hald" say that hald is running and a "ps -ef|grep hald" show that it is running with a --drop-privilege parameter and as a "hal" user

I can mount and access my pen drive and my photo camera, so hald is running and working. I suppose that problem is in --drop-privilege parameter as automount require a /etc/fstab modification

I am no able to find in /etc/init.d where hald is started

Regards
Franco Spinelli

---

### Post by frspin on 2004-12-11
After a lot of test I think that my problem is a "no feature" of Ubuntu Warty
I have installed Warty in a Vmware istance under Linux and under XP and also in a disk partition.
In all installations I can mount my CDROM "by hand", I have no automount and no auto browse of CDROM (audio e/o data).
Pen drive and photo camera work ok

I have also installed FC3 on same machine, in a instance of Vmware and in a disk partition. In all FC3 installation my CDROM work ok, with automount and auto browse.

Finaly I have upgraded a Warty installation (under Vmware in Linux) to Hoary, with full update at today. Now, in this installation, my CDROM work ok.

So, I suppose, there is a problem with Warty version on Gnome (gnome-volume-manager) and hal/dbus, solved in current Hoary version.

In this a bug?

Regards
Franco Spinelli

---

### Post by kamstrup on 2004-12-13
This is probably some kind of bug, but as long as it is solved in Hoary I think we should be grateful. There has been many problems related hal/dbus but this is probably mostly because they are brand new in Gnome 2.8. I expect much better hal/dbus integration with Gnome 2.10  .

---

### Post by irielion on 2005-08-09
I figured out how to remove the --drop-privileges...
It all starts in /etc/init.d/dbus-1, then it goes all the way up to /etc/dbus-1/event.d/hal*
and you end up in /etc/defaults/hal, remove DAEMON_OPTS

---


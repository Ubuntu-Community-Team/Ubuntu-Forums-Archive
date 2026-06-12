---
title: "CDs won't always automount"
date: 2005-10-22
forum: Desktop Environments
---

### Post by orzechowskid on 2005-10-22
There's something going on between my DVD drive and Ubuntu, where CDs don't always get automounted.  Sometimes they do, and sometimes they don't.  It happens with data CDs, audio CDs, and PSX game discs, either pristine or all scratched up.  One time I'll stick in a CD, read from it, and eject it by right-clicking on its desktop icon, and the next CD won't do anything.  I try mounting it from the command line, and the process becomes uninterruptable and locks up the console I ran it from.  Sometimes I'll stick a CD in and hear the drive whir a little then spit the CD back out at me.

I'm using a Pioneer slot-loading DVD drive on Breezy.  I've never had any problems with it and it still works perfectly if I boot into Windows, so I don't think it's related to the drive itself.

Anyone have any idea what's going on here, or things I can look at to get more information?

thanks

---

### Post by grj on 2005-10-22
Are you sure you are having trouble mounting data CDs and not having trouble when mounting music CDs? I ask this because factory music CDs are not mountable as they do not have a file system. I cannot speak to psx game disks.

---

### Post by orzechowskid on 2005-10-22
I don't think it's a problem of audio CDs not having a filesystem.  I can put audio CDs in my drive and have them show up as an icon on my desktop (sometimes).  When they show up on the desktop I can play them and rip them in grip, and browse them in Nautilus.  Same with data CDs; if everything is working then I can put the disc in the drive and have an icon appear on my desktop and browse with Nautilus.

Most of the time, I put a disc in the drive and nothing happens.  The drive does not make noises like it does when spinning up the disc to mount it.  This is what usually happens, with both audio and data CDs.

---

### Post by pecanov on 2005-10-22
I'm having a similar problem, except in my case it's obvious there is a problem with reading a  cd ... sometimes it takes 2-3 minutes of torturing my drive and failing, and other times it will mount it successefully in 2 seconds! (using the same media).

Hmm... it seems it's HAL ... stopping the automount and mounting as root always works.

---

### Post by orzechowskid on 2005-10-30
so how do I turn off HAL?  it's not one of the services listed in the GNOME services applet, and though I know how to manually do it by poking around in /etc/init.d , what's the 'real' way to do it?

---

### Post by Kasanax on 2006-01-14
I've been having a similar issue... data CDs tend to work fine (they automount, usually, or i can manually mount them), but music CDs won't automount. When I try mounting one manually, I get this error message:

```
mike@ubuntu:~$ sudo mount /dev/scd0
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```


Checking dmesg, I get this:

```
[4295944.156000] end_request: I/O error, dev sr0, sector 64
[4295944.157000] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16

```

Any thoughts? :confused:

---

### Post by phpmonkey on 2006-02-04
Hi everybody \\:D/ 

I have a similar problem to kabanax.

Data CDs work fine for me, but audio CDs will notdo anything (not recognised), and I get the following error:

> mount: block device /dev/hda is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

The syslog had this to say...

> [4298491.335000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4298491.335000] hda: command error: error=0x50 { LastFailedSense=0x05 }
[4298491.335000] ide: failed opcode was: unknown
[4298491.335000] end_request: I/O error, dev hda, sector 64
[4298491.336000] isofs_fill_super: bread failed, dev=hda, iso_blknum=16, block=16

And fstab....

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


I know this problem crops up, I've been hunting google and these very forums for an answer, but haven't come across a satisfactory one yet.

Any help would be very appreciated! :p

---

### Post by phpmonkey on 2006-02-05
Not to worry, It started working automagically.

I must have appeased the voodoo goods ;)

[I installed some other packages, I guess one of them triggered something...)

---

### Post by dcstar on 2006-02-05
[QUOTE=phpmonkey]Not to worry, It started working automagically.

I must have appeased the voodoo goods ;)

[I installed some other packages, I guess one of them triggered something...)[/QUOTE]
Automounting is still flaky in Breezy (in my own personal experience, as well as others who have posted similar problems), hopefully the Dapper version will improve things.

---

### Post by Kasanax on 2006-02-06
PHPMonkey - what packages was it that you installed?

I currently have my sound running through my CD player/stereo, but I'm replacing it with a new set of Bose speakers next week, and I need to be able to play my CDs (or at least rip them to my HD) without an external CD player... so I'm starting to get desparate! :cry: 

Any advice would be greatly appreciated!

---

### Post by Kasanax on 2006-02-14
Problem solved... don't I feel silly? :oops: 

So, I've finally come to understand that audio CD's don't need to be mounted. If I just put the CD in the drive, and open some program that can read/play/rip (i.e. Goobox), I can see the files just fine.

---

### Post by ispmarin on 2007-02-20
> **phpmonkey said:**
> Hi everybody \\:D/ 

I have a similar problem to kabanax.

Data CDs work fine for me, but audio CDs will notdo anything (not recognised), and I get the following error:



The syslog had this to say...



And fstab....



I know this problem crops up, I've been hunting google and these very forums for an answer, but haven't come across a satisfactory one yet.

Any help would be very appreciated! :p

Having exactly the same error here. It is more constant than this, but sometimes I can`t mount the drive at all. I have also some problems on the boot process, it took WAY too long to boot from a cd. Sometimes nautilus says that the data on the cd/dvd is corrupted. Starting to think that this is a hardware error... my drive is a LG h20n. Anyone?

---

### Post by orb9220 on 2007-02-20
This thread is a year old. You may want to start a new thread yourself.

---

### Post by neogus on 2007-08-29
Ok i have the same problem whit the same dvd drive. GSA-H20N. Ubuntu recognizes the drive but im unnable to mount it. I really need help on this because i cant do anything whitout this drive. I have the last version 7.04.

---


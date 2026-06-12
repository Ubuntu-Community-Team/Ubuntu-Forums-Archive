---
title: "can't boot .... help folks... (could be simple).."
date: 2006-03-23
forum: Desktop Environments
---

### Post by dotdot on 2006-03-23
ok here's the story...

i modified (only slightly)../etc/init.d/rcS

now the box won't boot.

hangs at checking battery state...

All i want to do now is go back - and move the old file back - .... how do you do it .. ?

I've booted into recovery mode & can see the files - and can't 
do anythnig as it's (/ fs is.. )  mounted ..read only.

..Can anyone help (this has got to be possible / pretty simple to fix..)

..

---

### Post by Q4U on 2006-03-23
If you have the Live CD it's really easy: boot the PC from the CD (change the BIOS boot priority so that the CD comes before the HDD), then mount the filesystem* and restore the offending item. Q

* System -> Administrator -> Disks

---

### Post by dotdot on 2006-03-23
only prob is (right now) I don't have the livecd ....(to hand)..

any other ideas....



otherwise I'll have to dl then burn then do this much later.

..

---

### Post by Q4U on 2006-03-23
I assume you have an internet connection and another PC working (otherwise you wouldn't be posting, right?!).

If I were you, I would download a minimal linux system. Dowloading a whole 600MB of live CD and burn it for a one-minute recovery job is a bit of an hassle.

Two quick and easy possibilities come to mind:
1. floppy-disc (less than 2MB download): [http://www.toms.net/rb/](http://www.toms.net/rb/)  - Note: you have to work with the command line (you just need the mount and rm commands, so even if you are no guru it should be feasible) and have a floppy (some new systems don't). 
2. USB, like [www.damnsmalllinux.org/](www.damnsmalllinux.org/) or [www.puppyos.com](www.puppyos.com) (50MB) Note: you have to have a USB stick handy and a PC that can boot from it (most modern mobos can).

Let me know if any of these two solutions are feasible for you.  Q

---

### Post by dotdot on 2006-03-23
ok i've downloaded.. burned now trying to boot.

this failed (media problems?) - i'm now in what looks like a makeshift shell.

..I can't seem to see all devices to mount up... any ideas ?

..laptop layout

win2k
ubuntu 5.10

hda1was win 
hda8 was i think breezy.

..suggestions welcome ....

---

### Post by Q4U on 2006-03-23
What exactly did you download, the liveCD or any of the 1. or 2.? If it's the floppy, it is normal to be dropped in a shell. 

If it's the live CD (i guess that this is the case), there might be a problem with the media (have you verified the md5sum?). But in any case, even if X failed  but there is a bash shell available, then you try:

sudo mkdir /media/recover
sudo mount /dev/hda8 /media/recover -t ext3 umask=022

(this assumes that hda8 is ext3: replace with the actual filesystem of your partition) Q

---

### Post by vidak on 2006-04-04
[QUOTE=dotdot]ok here's the story...

i modified (only slightly)../etc/init.d/rcS

now the box won't boot.

hangs at checking battery state...

All i want to do now is go back - and move the old file back - .... how do you do it .. ?

I've booted into recovery mode & can see the files - and can't 
do anythnig as it's (/ fs is.. )  mounted ..read only.

..Can anyone help (this has got to be possible / pretty simple to fix..)

..[/QUOTE]

it's quite easy to fix this read-only problem, eg.:
mount /dev/hda1 / -o rw,remount

another tricky thing - if even recovery mode won't work, you can enter a boot option 
init=/bin/sh
in lilo/grub
and you get a bash prompt instead of the full boot (note that this can be a security problem, as you can get easily root-access this way)

---


---
title: "Doom and gloom re-installing Breezy..."
date: 2006-05-05
forum: Desktop Environments
---

### Post by pyromidget on 2006-05-05
Hi all - hope you'll be able to help with this one (and sorry for the long post, but i like detail)...

I had Breezy up and running fine, but realising that my box was a little on the noisy side, I wondered how I could re-arrange things inside to increase airflow (and decrease fan speed).

After around an hour of swapping around PCI cards, cleaning the caked-on layers of dust out of the filters and re-assembling the whole thing with less clutter, I realised that now would probably be a good time to do a re-install seeing as how I'd swapped out the graphics card and probably caused other sorts of chaos.

I hunted out the 'official' Breezy CD that I had around somewhere and set about the install.  Everything went well up until the 'Copying remaining Packages to Hard Disk' stage where all manner of errors came up (sadly can't remember what though).  I ran a disk integrity check and discovered that my shipit CD was rather unwell...

Fast-forward 40-ish minutes and a freshly-burned Breezy ISO pops out of my flatmate's computer.  This install went fine up until the point that the CD was ejected and the box rebooted.

> Grub loading...

Error 15

GRR!!! Now i'm starting to get pissed.  Google turned up this:

[B][I](15 : "Error while parsing number"

This error is returned if GRUB was expecting to read a numbur and encountered bad data.)[/I][/B]

I ran a check on the hard drive just in case using the SCSI BIOS, and the disk  media itself was fine.  I've tried re-running the installer a few times and get the same every time.

I'm not convinced it was all my swapping about etc that killed things as the disk portion of the installer completes fine, it just seemes to be GRUB that hates me ](*,)

Anyone got any ideas what might be wrong?

---

### Post by neouser99 on 2006-05-05
what does your menu.lst (grub.conf) look like?? is probably just trying to access something that doesn't exist, in which case you can just play with the numbers till you get one that works.

-neo

---

### Post by pyromidget on 2006-05-05
There's no way for me to check it that I can see.   When grub hangs there's not the usual prompt, it literally gives me:

> 
Verifying DMI Pool Data............
GRUB loading stage1.5.


GRUB loading, please wait...

Error 15
And stops there.

---

### Post by pyromidget on 2006-05-06
Sorry to bump this folks, but i really am stumped and need to get this box up and running.  I've tried following a few different guides on how to re-install GRUB using a live CD, but they all tell me to use the result from typing:

> grub> find /boot/grub/stage1
but all i get from that is:
>     GNU GRUB  version 0.95  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename. ]

grub> find /boot/grub/stage1

Error 15: File not found

People have also suggested using a GRUB boot floppy, but i don't even HAVE a floppy drive on this computer! ](*,)

Any ideas, folks?

---

### Post by Tachyon1000 on 2006-05-06
I had a very similar problem installing Ubuntu.  My comp is very old and the cd drive and/or the ide controller has been shaky for some time.  I was lucy to reach the same part of the installation that you reached before the install failed after many many tries.  Be that as it may, the only solution I can suggest is to keep trying to install the distro.  If it can get passed that step, the installation program can get the packages from over the web.  Seems strange that we both had the same problem.  Maybe a problem with the current iso that is being served up??

Anyway, I am using Ubuntu right now on that same computer so the problem is likely to be overcome with persistence.

---


---
title: "Backing up to CD"
date: 2005-12-10
forum: General Help
---

### Post by jonathanhayward on 2005-12-10
What is the preferred way to backup to CD?

I have a script I wrote which tars up, slices, and uses cdrecord; it presently isn't working because there is no /dev/cdwriter and I don't know how to make it.

What are the steps in getting cdrecord to work?

--or--

what is the preferred tool to backup a filesystem to CD?

-- 
++ Jonathan Hayward, [email]jonathan.hayward@pobox.com[/email]
** To see an award-winning website with stories, essays, artwork,
** games, and a four-dimensional maze, why not visit my home page?
** All of this is waiting for you at [http://JonathansCorner.com](http://JonathansCorner.com)

---

### Post by jonathanhayward on 2005-12-18
Are there no answers to this thread/question? I would really like to be able to back up my system to CD.

++ Jonathan Hayward, [email]jonathan.hayward@pobox.com[/email]
** To see an award-winning website with stories, essays, artwork,
** games, and a four-dimensional maze, why not visit my home page?
** All of this is waiting for you at [http://JonathansCorner.com](http://JonathansCorner.com)

---

### Post by schilcha on 2005-12-18
[QUOTE=jonathanhayward]Are there no answers to this thread/question? I would really like to be able to back up my system to CD.[/QUOTE]

Just to make things clear: I have never tried to get something like this running, so all I can tell you is what I would try to do ;-). Would like to help, since you've been waiting for a long time...

Anyways, have you tried running ```
sudo cdrecord -checkdrive
```
For me, it identifies the cd-burning device correctly. (It also works without sudo, but the I get a warning/error message)

Searching for "backup cd" in synaptic will generate some hits that look promising for you. (e.g. cdbackup or multicd)

---

### Post by Ben Armston on 2005-12-18
[QUOTE=jonathanhayward]What is the preferred way to backup to CD?

I have a script I wrote which tars up, slices, and uses cdrecord; it presently isn't working because there is no /dev/cdwriter and I don't know how to make it.

What are the steps in getting cdrecord to work? [/QUOTE]

I've had success using

```
sudo cdrecord dev=/dev/hdd speed=4 image.iso
```

obviously you'll need to change the device and iso image.  cdrecord does complain about using the device directly but it still works.

Ben.

---

### Post by jonathanhayward on 2006-03-14
Thank you. I tried it and got i.e.

root@inner-sanctum:/scratch# cdrecord dev=/dev/cdrw -data cdimage29117.iso
cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.12-10-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/cdrw'
devname: '/dev/cdrw'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'ubuntu-0.8ubuntu1'.
cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'TEAC    '
Identifikation : 'CD-W28E         '
Revision       : '2.1A'
Device seems to be: Generic mmc CD-RW.
cdrecord: Cannot load media with this drive!
cdrecord: Try to load media by hand.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R
cdrecord: Cannot load media with this drive!
cdrecord: Try to load media by hand.
cdrecord: Cannot load media.

++ Jonathan Hayward, [email]jonathan.hayward@pobox.com[/email]
** To see an award-winning website with stories, essays, artwork,
** games, and a four-dimensional maze, why not visit my home page?
** All of this is waiting for you at [http://JonathansCorner.com](http://JonathansCorner.com)

---


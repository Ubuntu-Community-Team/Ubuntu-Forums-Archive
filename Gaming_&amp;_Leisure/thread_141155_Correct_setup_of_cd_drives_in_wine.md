---
title: "Correct setup of cd drives in wine"
date: 2006-03-07
forum: Gaming &amp; Leisure
---

### Post by patbuntu on 2006-03-07
I'm using wine 0.99 and every app I try and run that expects a cd can't find it even though it is in the drive.

winecfg autodetects the following:
C: ../drive_c
D: /media/cdrom0
E: /media/cdrom1
F: /media/floppy0
H: /home/pat
Z: /

If I install a game from cd, either by running wine /media/cdrom0/whatever.exe or wine ~/.wine/dosdevices/d:/whatever.exe the install seems to work fine.  Whenever I try and run the installed game I never get further than a 'Insert cd' type prompt, even though the cd is inserted and mounted.

Should I have a ~/.wine/drive_d as well?  If I should how do I map that to the same place as /media/cdrom0?  Am I doing something fundamentally wrong?

I've also tried copying the cd contents to my hard drive (straight file copy) and mapping that to D: instead.  That didn't work, but I wasn't expecting it to anyway.

For the record I'm trying this with Caesar 3 and Settlers 4, both listed as working in the wine apps database.

Any suggestions most welcome.

-Pat

---

### Post by colo on 2006-03-07
I suppose those titles feature some vile copy-protection-scheme, which will not be satisfied by some files looming around somewhere in your filesystems alone.
There used to be a device="..."-directive in wine's config a year or so ago, to tell wine where to look for the actual physical disk to gain blockwise access to the inserted media (what is mandatory for most copy-protection-systems to allow you to run the software they protect), but it's been long ever since I used it - and so much in wine's config has changed, I don't even know for sure if this possibility still exists...

I'm sorry I'm unable to help you any further, but I'm sure others will do.

If not, give the Cedega-demo a shot. 15 days to test, 15 bucks to pay if you'd like to use t for a longer time.

---

### Post by patbuntu on 2006-03-07
Thanks for the reply.  I tried the cedega demo but didn't get any further unfortunately, I couldn't even get the installer to run properly (the windows exe that is, cedega installed fine).  The device= command sounds similar to the mappings I have in winecfg, but even if the cds are copy protected (which I'm sure they are) having the physical disc mounted should get around this shouldn't it?  Or is wine only usable for apps which do not require the physical media to run?

-Pat

---

### Post by colo on 2006-03-08
Copy protections work in a way that they scan the physical media of the disc for errors on certain sectors, which are placed on certain locations deliberately. However, when a disc gets mounted, and some program read()s a file on the mountpoint, the error-correction of the drive immediately kicks in, and the function returns a value other than when directly accessing a bad sector - the copy protection fails, and your app is disallowed to start.

In case the application has access to the actualy device (which it has under windows, because of this system's poor security and overall design), it just uses raw device access to collect the information about the sectors in question, and everything will be fine.

This is possible with GNU/Linux, too - but NOT if the programs does now of the filesystem only, and nothing about the disc.

---

### Post by beast2k on 2006-03-08
I know this does not help but I have that problem with crossover office, Cedega,  and wine. Even though the cd's work fine in ubuntu it turns out the distro itself is the only thing that can see the cd's and Dvd's etc properly. I was told that it may have something to do with the fact that things are mounted in /media and not in /mnt as is normally the case and most apps expect media to be mounted in /mnt. I don't know if there is any truth to this but I have found no info on it just more people with the same problem.

---

### Post by patbuntu on 2006-03-08
So would there be a difference in the way that a drive mounted under /media/... would be seen compared to a drive mounted to /mnt/... ?  I thought that when you mounted a drive it just became part of the filesystem. 

If the app was attempting to access the drive and deciding the copy protection check failed for whatever reason, then surely the drive would spin up.  So I think this is more an issue with wine not seeing the drive than anything else...

-Pat

---

### Post by polpak on 2006-03-08
[QUOTE=patbuntu]I'm using wine 0.99 and every app I try and run that expects a cd can't find it even though it is in the drive.

(SNIP)

If I install a game from cd, either by running wine /media/cdrom0/whatever.exe or wine ~/.wine/dosdevices/d:/whatever.exe the install seems to work fine.  Whenever I try and run the installed game I never get further than a 'Insert cd' type prompt, even though the cd is inserted and mounted.

(SNIP)

Any suggestions most welcome.

[/QUOTE]


This is pretty easily solved. Wine supports copy protection. Just go to winecfg to the drives tab, select the drive for your CD rom, and click the advanced button. Change the type from "Automatic" to "CDROM". And it should enable the copy protection tests.

---

### Post by beast2k on 2006-03-08
[QUOTE=patbuntu]So would there be a difference in the way that a drive mounted under /media/... would be seen compared to a drive mounted to /mnt/... ?  I thought that when you mounted a drive it just became part of the filesystem. 

If the app was attempting to access the drive and deciding the copy protection check failed for whatever reason, then surely the drive would spin up.  So I think this is more an issue with wine not seeing the drive than anything else...

-Pat[/QUOTE]
There shoulden't be a difference at all mounting is mounting and a mount point is a mount point. It doesn't make sence, I thought these types of apps autodetected the media and mount points. Apps for me have big problems using the cdrom but ubuntu itself works with all the media etc perfectly, I do recall this problem some time ago with mandrake 8.2 I think but they did fix it. It had something to do with automount or supermount I cant remember. I don't know what it is thats going on but there is a problem. Can anyone shed some light on this ? If ubuntu uses all the drives just fine how can I report it as a bug?

---

### Post by patbuntu on 2006-03-08
[QUOTE=polpak]This is pretty easily solved. Wine supports copy protection. Just go to winecfg to the drives tab, select the drive for your CD rom, and click the advanced button. Change the type from "Automatic" to "CDROM". And it should enable the copy protection tests.[/QUOTE]

This was exactly what was needed - thanks very much.  Works perfectly now :D

[QUOTE=beast2k]Apps for me have big problems using the cdrom but ubuntu itself works with all the media etc perfectly, I do recall this problem some time ago with mandrake 8.2 I think but they did fix it.[/QUOTE]

This had also worked previously for me straight away with SUSE 9.3 - so is it a Ubuntu problem that needs reporting or not?

Thanks very much for everyones help

-Pat

---

### Post by beast2k on 2006-03-09
[QUOTE=patbuntu]This was exactly what was needed - thanks very much.  Works perfectly now :D



This had also worked previously for me straight away with SUSE 9.3 - so is it a Ubuntu problem that needs reporting or not?

Thanks very much for everyones help

-Pat[/QUOTE]
I honestly don't know if it's a bug or not, ubuntu works fine with it's cdroms/dvds but other progs/apps do not, is it ubuntus problem or other apps problem? Judging by the floppy/zip pmount bug and the problems with that I would not be suprised if there's a small bug with the cd/dvd side of things. As long as there is a work around for the bug/problem I can wait for the new version, it's so close I can't wait to get rid of all these minor problems.

---

### Post by Z3PX on 2006-08-26
I had the same problem. Went into winecfg, autodetected the drives, selected the /media/cdrom drive. Went into advanced options and set "type" as cd-rom.
Work perfect after that.

---


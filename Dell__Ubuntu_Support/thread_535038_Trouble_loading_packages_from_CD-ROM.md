---
title: "Trouble loading packages from CD-ROM"
date: 2007-08-26
forum: Dell  Ubuntu Support
---

### Post by eisenstein on 2007-08-26
Hi all-

I'm having trouble loading packages from the Ubuntu 7.04 CD.  My setup is a Dell 1420 Inspiron (brand new) that came with Ubuntu 7.04 pre-loaded.  I'm new Linux, but learning fast.

The original problem was that gcc comes pre-loaded, but the standard header files (like stdio.h) aren't loaded.  From past threads here I learned I had to do an install like:

        sudo apt-get install build-essential

This led to the CD-ROM problems I need help with.
[I need to install from the CD-ROM because the wireless connection is not working with Firefox for some reason-- one thing at a time...]

Anyway, my first attempt was through Synaptic.  But nothing like gcc-dev or build-essential was listed.   And all packages listed are already installed.

So with Ubuntu CD in the drive, I tried in Synaptic:

     Edit->Add CDRom

Got this error message:

E: Failed to mount the cdrom.

I know the system is reading the CD-ROM because I can browse its contents.  There is indeed a build-essentials directory:

/media/"Ubuntu 7.04 i386"/pool/main/b/build-essential

 I'm guessing the problem is that Synaptic isn't finding it.  So I switched to the shell command liine to try and track it down.

First attempt:
     sudo apt-get install build-essential
Gives error message:
    E: Couldn't find package build-essential
No surprise.  I edited the /etc/apt/sources.list by uncommenting the obvious line starting with deb cdrom:  But got the same error.

so I tried:
     sudo apt-cdrom add
and got this output:

Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
E: Failed to mount the cdrom.

I went looking for the devices in question.  
The relevent output of "ls -al / " was:
lrwxrwxrwx   1 root root    11 2007-08-25 01:15 cdrom -> media/cdrom

and of "ls -al /media":
lrwxrwxrwx  1 root root     6 2007-08-25 01:16 cdrom -> cdrom0
drwxr-xr-x  2 root root  1024 2007-06-21 07:12 cdrom0
dr-xr-xr-x 13 ben  root  4096 2007-04-15 06:52 Ubuntu 7.04 i386

The last entry there is the actual CD.  So it looks like /cdrom isn't pointing to the right place.  Here's the relevent output of mount:

/dev/hda on /media/Ubuntu 7.04 i386 type iso9660 (ro,nosuid,nodev,uid=1000,utf8)

In fact, in /dev each of cdrom, cdrw and dvd point to /dev/hda
So should I be trying to mount from /dev/cdrom instead of /cdrom?
I'm past my level of competence here, but I did check /etc/fstab and found nothing that looked like what I needed.  All it had was:

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

Which I already know isn't connected to the drive where the disk is.

Can anyone tell what's going on here?  How can I fix it?

Ben

---

### Post by logos34 on 2007-08-26
First of all, build-essential package is inside folder of same name, so you might want to manually copy 'build-essential_11.3_i386.deb' to your home folder and install it from there.  You can then move the deb to /var/apt/cache/archives, which is where all the other debs are stored.

Part of what's happening with the cdrom I think is that the Feisty libata driver subsystem detects everything as scsi devices--hence the '/dev/scd0' entry in fstab (at least this is how it was seen at install time).  But for some reason the symlinks in the /dev directory are pointing to 'hda'.  However it should be mounting at '/media/cdrom0', that I am pretty sure of.  Try changing fstab to read '/dev/hda'.  Or make the symlinks point to '/dev/scd0'.

---

### Post by eisenstein on 2007-08-26
Thank you!

I changed the fstab entry from /dev/scd0 to /dev/hda.  After that I was able to use sudo apt-cdrom add and synaptic to add the build-essential package.

I'm thinking that since this is a problem with the pre-installed Ubuntu 7.04 on a Dell 1420, it would be good to get this fix to someone in a position to change it at the level of Dell's installation.  Otherwise everyone who buys a Dell Ubuntu 1420 and needs to load additional packages from the CD is going to go through the same hassle.

I'll see what I can do about making this happen-- but I'm new here, so any pointers on where to go and what to do are appreciated.

Ben

---

### Post by logos34 on 2007-08-26
> **eisenstein said:**
> Thank you!

I changed the fstab entry from /dev/scd0 to /dev/hda.  After that I was able to use sudo apt-cdrom add and synaptic to add the build-essential package.

I'm thinking that since this is a problem with the pre-installed Ubuntu 7.04 on a **Dell 1420, it would be good to get this fix to someone in a position to change it at the level of Dell's installation.  Otherwise everyone who buys a Dell Ubuntu 1420 and needs to load additional packages from the CD is going to go through the same hassle.**

I'll see what I can do about making this happen-- but I'm new here, so any pointers on where to go and what to do are appreciated. 

Ben

Agreed.  I'd contact the forum mods, see what they recommend.  You could go directly to Dell, but I don't know what dept--might just get lost in that bureaucratic black hole.  There is a linux forum over there...I just did a quick search and [pulled up this]("http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&message.id=2126&query.id=273850#M2126") (there are apparently others)

---


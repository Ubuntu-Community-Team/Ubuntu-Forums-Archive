---
title: "Upgrading to Dapper 6.06?"
date: 2006-08-11
forum: Desktop Environments
---

### Post by Cloudy on 2006-08-11
So I've been running on Breezy for a while but recently I got my 6.06 CDs in the mail. (Well, Kubuntu 6.06..) I figured if downloaded kdesktop and everything and then popped the Kubuntu CD in the CD-ROM drive, I could open Synaptic or KPackage and add the Kubuntu 6.06 CD to the repositories. However, I can't. When I try to add to the repositories, Breezy Badger, updates, & security updates are still listed in the dropdown box. 

I'm not sure what to do..
I thought sudo apt-get update would bring my system up to date, but I was apparently wrong or I did something wrong somewhere.

I'm confused..
](*,)

---

### Post by Ramses de Norre on 2006-08-11
Change all instances of 'breezy' in  /etc/apt/sources.list to 'dapper' then pop in the cdrom and do ```
sudo apt-cdrom add
``` finally you do ```
sudo aptitude update && sudo aptitude dist-upgrade
```

---

### Post by Cloudy on 2006-08-11
Alright, thanks I changed all those instances to dapper - is there anything I ought to do now?

> 

Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-ROM...
Identifying.. [d251c204c5513e9470c11bf645950d27-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes and 1 signatures
This disc is called:
'Kubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)'
Copying package lists...gpgv: Signature made Tue 30 May 2006 10:33:59 PM CDT usi                                           ng DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu                                           .com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Kubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main r                                           estricted
Unmounting CD-ROM...Repeat this process for the rest of the CDs in your set.
travis@ubuntu:~$ sudo aptitude update && sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
The following packages have been kept back:
  cpp cpp-4.0 g++ g++-4.0 gcc gcc-4.0 libc6-dev libstdc++6-4.0-dev wine
0 packages upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
travis@ubuntu:~$      


I just checked the repositories in Synaptic and it still lists the breezy CDs?

---

### Post by Ramses de Norre on 2006-08-11
Can you post you sources.list? I think there is something wrong in there..

---

### Post by Cloudy on 2006-08-11
Sure thing.

> 
deb cdrom:[Kubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main



aaaaand that's it.

---

### Post by Ramses de Norre on 2006-08-11
You've commented everything out??
Change it to this: ```
deb cdrom:[Kubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

deb http://wine.budgetdedicated.com/apt dapper main
```

Then run ```
sudo aptitude update && sudo aptitude dist-upgrade
``` again.

---

### Post by Cloudy on 2006-08-11
wait.. o.o
It is all commented out. I just noticed that (yeah, I'm slow. >.>) That's really, really peculiar because I don't have any memory of doing such nor is there anyone else around here that uses Ubuntu or Kubuntu on this particular PC..

but yeah, thanks!

---

### Post by Ramses de Norre on 2006-08-11
Use the one I gave you because you missed a lot of binary repos too, you only had the source ones.

---

### Post by Cloudy on 2006-08-11
Gotcha. Thanks again.

---

### Post by az on 2006-08-11
> **Cloudy said:**
> So I've been running on Breezy for a while but recently I got my 6.06 CDs in the mail. (Well, Kubuntu 6.06..) I figured if downloaded kdesktop and everything and then popped the Kubuntu CD in the CD-ROM drive, I could open Synaptic or KPackage and add the Kubuntu 6.06 CD to the repositories. However, I can't. 

The shitpit CDs are the Desktop cd - they are live CDs.  They are not a repository of packages like the alternate (text-mode installer) cds.

You cannot upgrade from them since they are a complete live filesystem which gets transplanted back onto your hard disk when you install (and not a disk full of individual packages)

There is a tiny repo on the disk which holds build-essential and linux-headers and stuff, but not much else.

---

### Post by Cloudy on 2006-08-12
Ahhhh.
I see.

I'm having some weird problems now, though..

Like, I have 6 different Ubuntu options on GRUB. 2 sets of 3 of the same thing, if that makes sense at all.

And whenever I go to shut down, for a few seconds my monitor displays a bunch of jarbled characters and then goes to the Ubuntu loading splash before shutting down. I don't think it's anything that's going to affect my system, but I'm kind of curious and it's a little irritating just knowing that something's wrong but I don't know what. >_<

---

### Post by Ramses de Norre on 2006-08-12
> **Cloudy said:**
> 
Like, I have 6 different Ubuntu options on GRUB. 2 sets of 3 of the same thing, if that makes sense at all.
That's normal, you have more than one kernel installed and everyone of them has a normal and a recovery mode. You can remove some kernels if you like.

> **Cloudy said:**
> And whenever I go to shut down, for a few seconds my monitor displays a bunch of jarbled characters and then goes to the Ubuntu loading splash before shutting down. I don't think it's anything that's going to affect my system, but I'm kind of curious and it's a little irritating just knowing that something's wrong but I don't know what. >_<
Happens here too.. guess that's normal too.

---

### Post by Cloudy on 2006-08-12
Alright, but how do I remove those other kernels? 

Does linux-image have anything to do with it?

---

### Post by Cloudy on 2006-08-12
I'm gonna take a chance and hope what I found on Google is right.. I guess just remove one of the linux-images from KPackage or Synaptic.

---

### Post by az on 2006-08-12
> **Cloudy said:**
> I'm gonna take a chance and hope what I found on Google is right.. I guess just remove one of the linux-images from KPackage or Synaptic.

You can remove all but one (you need one kernel to boot into)

---

### Post by maniacmusician on 2006-08-12
i think if you download the alternate CD, that has a lot of stuff on it. I remember one time I installed an oem version and it loaded a lot of stuff from the CD (didnt have an internet connection so i know it was from CD).

---

### Post by Cloudy on 2006-08-13
@azz: Yeah. I got that much. ;o I wound up removing the old kernel. Bit peculiar, but I get errors with cupsys and some other programs whenever I try to uninstall/install programs. I'll get a screencap the next time I try to install something.. everytime it says that the installation may not have been completed etc. because of cupsys and these other programs.

---

### Post by Ramses de Norre on 2006-08-13
> **azz said:**
> You can remove all but one (you need one kernel to boot into)

I'd keep at least two kernels, doing that has saved my system more then once yet.
And if it annoys you, you can remove the recovery mode entries to get less grub entries.

---

### Post by Cloudy on 2006-08-13
Ahh, I screwed up somewhere. 8) (I'm really good at that.. I'm just getting the ropes of how to handle KDE and stuff. I'm used to GNOME but I want to give KDE a go right now) 

but yeah..
I used to be able to open the KMenu and go to System (right under the 'Actions' bar, not the one that houses KPackage/KSysGuard/etc.) > Appearance & Themes, but I was just messing with some preferences and I changed the panels around a bit but I guess along the way I changed something else, too, because now when I open the KMenu the "System" menu is gone so I can't get to Appearances & Themes now. Where did I mess up? XD

Also:
> 
I get errors with cupsys and some other programs whenever I try to uninstall/install programs. I'll get a screencap the next time I try to install something.. everytime it says that the installation may not have been completed etc. because of cupsys and these other programs.


[http://i8.tinypic.com/24gog13.png](http://i8.tinypic.com/24gog13.png) That's what I'm talking about.

---

### Post by az on 2006-08-13
> **Ramses de Norre said:**
> I'd keep at least two kernels, doing that has saved my system more then once yet.
And if it annoys you, you can remove the recovery mode entries to get less grub entries.

You only need one.  That's like saying you want to keep two copies of firefox installed just in case....


Of course, you need to boot into your new kernel before removing the old one, in case you installed the wrong kernel and you can no longer boot.

---

### Post by Cloudy on 2006-08-14
Eh if anything I can fallback on XP >.>

---


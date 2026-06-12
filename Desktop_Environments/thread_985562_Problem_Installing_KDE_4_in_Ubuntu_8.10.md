---
title: "Problem Installing KDE 4 in Ubuntu 8.10"
date: 2008-11-17
forum: Desktop Environments
---

### Post by N2G(bn#7+ on 2008-11-17
Hi, really simple question here hopefully: 

I'm trying to install KDE 4 on Ubuntu 8.10 - looks like the way you're supposed to do that is through the kubuntu-desktop meta package, but when I try that, it conflicts with the displayconfig-gtk and guidance-backends packages - I don't want to lose my nice automatic monitor set-up & detection under Gnome... 

What can I do?

Thanks,
Erland.

---

### Post by aysiu on 2008-11-17
Package conflicts generally come about from bad /etc/apt/sources.list files.

Can you paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here? ```
cat /etc/apt/sources.list
sudo apt-get update
``` (Make sure Synaptic, Update Manager, and Add/Remove are closed before you run them).

---

### Post by N2G(bn#7+ on 2008-11-17
Yep, here's the output:

Of cat /etc/apt/sources.list:
```
# added by the release upgrader
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main restricted
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://au.archive.ubuntu.com/ubuntu/ intrepid restricted main multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ intrepid-updates restricted main multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ hardy-updates restricted main universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://au.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://au.archive.ubuntu.com/ubuntu/ intrepid-security restricted main multiverse
# deb-src http://security.ubuntu.com/ubuntu hardy-security restricted main universe #Added by software-properties
deb http://au.archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://linux.getdropbox.com/ubuntu intrepid main
```

And of sudo apt-get update:
```
Ign http://linux.getdropbox.com intrepid Release.gpg
Ign http://linux.getdropbox.com intrepid/main Translation-en_AU
Get:1 http://au.archive.ubuntu.com intrepid Release.gpg [189B]
Ign http://linux.getdropbox.com intrepid Release  
Ign http://linux.getdropbox.com intrepid/main Packages
Ign http://au.archive.ubuntu.com intrepid/restricted Translation-en_AU
Hit http://linux.getdropbox.com intrepid/main Packages
Get:2 http://au.archive.ubuntu.com intrepid/main Translation-en_AU [2734B]
Ign http://au.archive.ubuntu.com intrepid/multiverse Translation-en_AU
Ign http://au.archive.ubuntu.com intrepid/universe Translation-en_AU
Get:3 http://au.archive.ubuntu.com intrepid-updates Release.gpg [189B]
Ign http://au.archive.ubuntu.com intrepid-updates/restricted Translation-en_AU
Ign http://au.archive.ubuntu.com intrepid-updates/main Translation-en_AU
Ign http://au.archive.ubuntu.com intrepid-updates/multiverse Translation-en_AU
Ign http://au.archive.ubuntu.com intrepid-updates/universe Translation-en_AU
Get:4 http://au.archive.ubuntu.com intrepid-security Release.gpg [189B]
Ign http://au.archive.ubuntu.com intrepid-security/restricted Translation-en_AU
Ign http://au.archive.ubuntu.com intrepid-security/main Translation-en_AU
Ign http://au.archive.ubuntu.com intrepid-security/multiverse Translation-en_AU
Ign http://au.archive.ubuntu.com intrepid-security/universe Translation-en_AU
Get:5 http://au.archive.ubuntu.com intrepid Release [65.9kB]                   
Get:6 http://au.archive.ubuntu.com intrepid-updates Release [51.2kB]           
Get:7 http://au.archive.ubuntu.com intrepid-security Release [44.0kB]          
Get:8 http://au.archive.ubuntu.com intrepid/restricted Packages [8408B]        
Get:9 http://au.archive.ubuntu.com intrepid/main Packages [1256kB]             
Get:10 http://au.archive.ubuntu.com intrepid/multiverse Packages [199kB]       
Get:11 http://au.archive.ubuntu.com intrepid/universe Packages [4542kB]        
Get:12 http://au.archive.ubuntu.com intrepid-updates/restricted Packages [2447B]
Get:13 http://au.archive.ubuntu.com intrepid-updates/main Packages [50.8kB]    
Get:14 http://au.archive.ubuntu.com intrepid-updates/multiverse Packages [14B] 
Get:15 http://au.archive.ubuntu.com intrepid-updates/universe Packages [17.1kB]
Get:16 http://au.archive.ubuntu.com intrepid-security/restricted Packages [14B]
Get:17 http://au.archive.ubuntu.com intrepid-security/main Packages [12.8kB]   
Get:18 http://au.archive.ubuntu.com intrepid-security/multiverse Packages [14B]
Get:19 http://au.archive.ubuntu.com intrepid-security/universe Packages [5554B]
Fetched 6259kB in 2min10s (47.9kB/s)                                           
Reading package lists... Done
```

The only curly in there is dropbox & I really don't think that has dependency issues...

Any help appreciated.

---

### Post by aysiu on 2008-11-17
I don't really see anything alarming in there, but let's start with a fresh one just to be sure.

Let's back up the old sources.list ```
cp /etc/apt/sources.list /etc/apt/sources.list.original
``` edit the new sources.list ```
gksudo gedit /etc/apt/sources.list
``` In the text editor that appears, paste in ```
# deb http://archive.canonical.com/ubuntu intrepid partner

deb http://au.archive.ubuntu.com/ubuntu/ intrepid main universe restricted multiverse

deb http://au.archive.ubuntu.com/ubuntu/ intrepid-security universe main multiverse restricted

deb http://au.archive.ubuntu.com/ubuntu/ intrepid-updates universe main multiverse restricted

# deb http://packages.medibuntu.org/ intrepid free non-free 

deb http://linux.getdropbox.com/ubuntu intrepid main
``` then save and close ```
sudo apt-get update
sudo apt-get install kubuntu-desktop
``` Do those conflicts still remain?

---

### Post by N2G(bn#7+ on 2008-11-18
Yeah, the conflicts are still there. Any further ideas?

---

### Post by Alienhated on 2009-04-18
I'm having the same problem, I'm having 17 conflicts. help please

And with "cp /etc/apt/sources.list /etc/apt/sources.list.original" says that there isnt any package that coincides.

and doing the last things that aysiu said, appears damaged packages something about dependencies.

---


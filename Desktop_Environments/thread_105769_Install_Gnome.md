---
title: "Install Gnome?"
date: 2005-12-19
forum: Desktop Environments
---

### Post by Maelgwyn on 2005-12-19
I've installed Kubuntu Breezy Badger from a cd yesterday, and I have to admit it; I prefer Gnome..

How do I install the necessary files to run GDM and Gnome from now on? Is it just easier to download Ubuntu Breezy, and start from scratch again? :(

I've had issues with Adept, but it seems to be working now... :s

:)

---

### Post by Leif on 2005-12-19
sudo apt-get install ubuntu-desktop.

then choose gnome from the sessions menu at the login screen

---

### Post by Maelgwyn on 2005-12-19
That didn't work.... :confused:

```

Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list http://nz.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://nz.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://nz.archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package ubuntu-desktop

```

---

### Post by Maelgwyn on 2005-12-19
Just thought I'd chuck this in here as well, just in case it's not right!!

```

deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted   
deb http://nz.archive.ubuntu.com/ubuntu breezy main restricted 
deb-src http://nz.archive.ubuntu.com/ubuntu breezy main restricted  
## Major bug fix updates produced after the final release of the
## distribution. 
deb http://nz.archive.ubuntu.com/ubuntu breezy-updates main restricted 
deb-src http://nz.archive.ubuntu.com/ubuntu breezy-updates main restricted 
## Uncomment the following two lines to add software from the 'universe' 
## repository. 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## universe WILL NOT receive any review or updates from the Ubuntu security 
## team. 
# deb http://nz.archive.ubuntu.com/ubuntu breezy universe 
# deb-src http://nz.archive.ubuntu.com/ubuntu breezy universe  
## Uncomment the following two lines to add software from the 'backports' 
## repository. 
## N.B. software from this repository may not have been tested as 
## extensively as that contained in the main release, although it includes 
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review 
## or updates from the Ubuntu security team. 
# deb http://nz.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 
# deb-src http://nz.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse  
deb http://security.ubuntu.com/ubuntu breezy-security main restricted 
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted  
# deb http://security.ubuntu.com/ubuntu breezy-security universe
 # deb-src http://security.ubuntu.com/ubuntu breezy-security universe 

```

---

### Post by Maelgwyn on 2005-12-19
heh oops.... I went to the list of updated repositories, and now it's fine.... :oops:

---


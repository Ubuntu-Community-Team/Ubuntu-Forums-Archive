---
title: "Simple multimedia questions"
date: 2005-11-09
forum: Desktop Environments
---

### Post by geir2rs1 on 2005-11-09
Hi all,
I am still working on my Ubuntu system.
My simple problem this time is:

Which codecs do I install/and where do I find them to play mp3 files in xmms or totem or any other player? Totem complains that it lacks plugins/codecs but it doed not say which.

How do I get DVDs to play in MPLayer? I have win32Codecs in /usr/local/lib/codecs
Cannot play wmv files either.
#-o 

I have searched this forum, but I did not find anything. It is probably here, but I can`t find it.
Geir

---

### Post by 23meg on 2005-11-09
[http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs) for mp3
[http://www.videolan.org/libdvdcss](http://www.videolan.org/libdvdcss) for DVD

How exactly did you install w32codecs?

---

### Post by geir2rs1 on 2005-11-09
I downloaded essential-20050412.tar.bz2 from mplayerhq. untared it.
Created the codecs folder under /usr/local/lib.
Copied the files from my home folder.
Folder creation and copying using sudo ......

Geir

---

### Post by 23meg on 2005-11-09
Try undoing those operations and installing w32codecs from the plf repository; see [here.]("http://www.ubuntuforums.org/showthread.php?t=87946")

---

### Post by Hairy_Palms on 2005-11-09
if you havent already then sudo apt-get install totem-xine 
then you might need the codecs for quicktime etc, getit from
[http://www2.mplayerhq.hu/MPlayer/rel...050412.tar.bz2](http://www2.mplayerhq.hu/MPlayer/rel...050412.tar.bz2)
then extract them to the folder /usr/lib/win32

---

### Post by geir2rs1 on 2005-11-10
Hi
Thanks for the advises. I still got problems though, but this might give some more leads.
(I am sorry. This is way too much pasting from the command line. I would have edited it but I do not know what too leave out)
MPlayer plays mp3, but very very bad.
I have followed  this link from 23mpeg:   
23meg's Avatar
 
Status: (Online)
Posts: 1,023
Join Date: Mar 2005
Location: Istanbul
Ubuntu Breezy 5.10 User
	
Default Re: Simple multimedia questions - 23 Hours Ago
[http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs) and tried to follow the instructions

My sources.list looks like this:
***************************************
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
## Uncomment the following two lines to fetch updated software from the network
deb [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted

deb [http://splashy.alioth.debian.org/debian/](http://splashy.alioth.debian.org/debian/) unstable main

deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) breezy java

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports main universe multiverse restricted

***************************************

When I try to run "sudo apt-get install gstreamer0.8-plugins" I get the following message:
************'
geitho@tux:~$ sudo apt-get install gstreamer0.8-plugins
Reading package lists... Done
Building dependency tree... Done
gstreamer0.8-plugins is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
****************'

I have tried apt-get update without success. It returns:
******* ***
geitho@tux:~$ sudo apt-get update
Ign [http://download.skype.com](http://download.skype.com) stable Release.gpg
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:4 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) breezy Release.gpg [189B]
Get:5 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Ign [http://download.skype.com](http://download.skype.com) stable Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) breezy Release
Ign [http://download.skype.com](http://download.skype.com) stable/non-free Packages
Ign [http://ubuntu.tower-net.de](http://ubuntu.tower-net.de) breezy Release.gpg
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) breezy-updates Release
Ign [http://splashy.alioth.debian.org](http://splashy.alioth.debian.org) unstable Release.gpg
Hit [http://ubuntu.tower-net.de](http://ubuntu.tower-net.de) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://download.skype.com](http://download.skype.com) stable/non-free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) breezy/main Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) breezy/restricted Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) breezy/main Sources
Hit [http://ubuntu.tower-net.de](http://ubuntu.tower-net.de) breezy/java Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) breezy/restricted Sources
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) breezy/universe Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://splashy.alioth.debian.org](http://splashy.alioth.debian.org) unstable Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) breezy-updates/restricted Sources
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports Release
Ign [http://splashy.alioth.debian.org](http://splashy.alioth.debian.org) unstable/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/multiverse Packages
Hit [http://splashy.alioth.debian.org](http://splashy.alioth.debian.org) unstable/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/restricted Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports/restricted Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/main Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/universe Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/multiverse Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/restricted Packages
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports/main Packages
  404 Not Found
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports/universe Packages
  404 Not Found
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports/multiverse Packages
  404 Not Found
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports/restricted Packages
  404 Not Found
Fetched 6B in 2s (3B/s)
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/breezy-backports/main/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/breezy-backports/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/breezy-backports/universe/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/breezy-backports/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/breezy-backports/multiverse/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/breezy-backports/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/breezy-backports/restricted/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/breezy-backports/restricted/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
geitho@tux:~$
**********

I suspect that apt cannot fine some of the sites to connect to but I am totally green here.

Anyone?

:confused: 
Geir

---

### Post by Hairy_Palms on 2005-11-10
the mirrormax sites no longer exist, if you have the win32 codecs in /usr/lib/win32 then can you play them with totem-xine?

---

### Post by geir2rs1 on 2005-11-10
Thanks
That almost did the trick.
I removede the the mirrormax sites from sources.list and installed totem.xine. I also created /usr/lib/win32 and copied the codecs to this directory. Totem now played mp3 fine.
Off course... One good answer leads to another question.
I tried to play a DVD (Pink Floyd - Dark Side of the moon) Totem threw this in my fase: **The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?**
I could not find this using synaptic. Where do I fine this. (The movie did start but stoped after a few second)

:( 
Geir

---


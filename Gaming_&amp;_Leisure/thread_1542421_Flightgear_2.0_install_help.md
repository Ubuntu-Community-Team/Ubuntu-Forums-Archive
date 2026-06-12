---
title: "Flightgear 2.0 install help"
date: 2010-07-30
forum: Gaming &amp; Leisure
---

### Post by andthewicked on 2010-07-30
I've never had to make from binary before so I could use some help with this one. I'm trying to install fightgear 2.0 from a binary that I downloaded from there website there all in tar files. so I guess where should I extract the files to and how do I install it, ive looked online but couldn't find a good reference.

---

### Post by andthewicked on 2010-07-30
I also see that people are using this download and compile script, I don't know how to use that either, do you know how to install this thing manually?

---

### Post by Aaron7 on 2010-07-30
Currently there is no package for Flight Gear 2 as you may know. There is a guide on their wiki at [http://wiki.flightgear.org/index.php/Scripted_Compilation_on_Linux_Debian/Ubuntu](http://wiki.flightgear.org/index.php/Scripted_Compilation_on_Linux_Debian/Ubuntu) which is the compilation script people have been using. I followed the instructions on the guide and it seemed to be downloading and compiling fine - I stopped it as it does take a while.

Running these commands in the terminal should install Flightgear, Fgrun, FGCOM, Atlas and Terrasync without affecting other versions in the folder fgfs.

> mkdir ~/fgfs
cd ~/fgfs
wget [http://brisa.homelinux.net/fgfs/download_and_compile.sh](http://brisa.homelinux.net/fgfs/download_and_compile.sh)
chmod 755 download_and_compile.sh
sh download_and_compile.sh


To run FlightGear, you would then run:
> cd ~/fgfs
sh run_fgfs.sh

Some people say it works fine, while others are having problems. Good luck.

---

### Post by andthewicked on 2010-07-30
"I think this might have to do with an update issue I've been having but if you have any ideas there more then welcome."
 
 
for some reason I am getting this error message 
 
 
Asking your password to perform an apt-get update
[sudo] password for kyle: 
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty Release.gpg
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Translation-en_US
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Translation-en_US
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty Release 
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Packages 
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Packages
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Packages 
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Packages
Err cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Packages 
Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Packages
Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg 
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/multiverse Packages
W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
 
W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
 
E: Some index files failed to download, they have been ignored, or old ones used instead.
 
 
any ideas?

---

### Post by Aaron7 on 2010-07-30
It looks like that it is trying to install the packages from a CD. If you go to System > Admin > Software Sources, make sure CD is not checked. You want to be downloading the packages from the internet.

Another method I found is to do this in the terminal:

> gksudo gedit /etc/apt/sources.list

then put a # in front of line witch refers to the CD 

Save and close file.

Hope this helps.

---

### Post by andthewicked on 2010-07-30
now im getting this error message 

Asking your password to perform an apt-get update
E: Type 'Asking' is not known on line 1 in source list /etc/apt/sources.list

---

### Post by Aaron7 on 2010-07-30
Could you please post your sources.list contents?

---

### Post by andthewicked on 2010-07-30
#Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty Release.gpg
#Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Translation-en_US
#Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Translation-en_US
#Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty Release
#Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Packages
#Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Packages
#Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Packages
#Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Packages
#Err cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Packages
# Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
#Err cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Packages
# Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/multiverse Packages
 
W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i3$
 
W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/bin$
 
E: Some index files failed to download, they have been ignored, or old ones used instead.deb cdrom:[Ubuntu 9.04 _$
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic restricted main multiverse universe #Added by software-proper$
 
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates restricted main multiverse universe #Added by softwar$
 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
#Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty $
#Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/$
#Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/$
#Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty $
#Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/$
#Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/$
#Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/$
#Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/$
#Err cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/$
# Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update c$
#Err cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/$
# Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update c$
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg $
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US $
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg $
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
 
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
 
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security restricted main multiverse universe #Added by softwa$
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security multiverse
 
 
sorry I couldn't select everything so I had to copy each section, I'm getting frustrated I'm about to just reinstall but thank you for all your help

---

### Post by Aaron7 on 2010-07-30
It looks like there is something wrong in the sources file. 

My sources.list file looks like this:

> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-backports main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted universe multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) lucid-getdeb apps
deb-src [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) lucid-getdeb apps

I hope you can find a solution and eventually have some fun on FlightGear ;) Good luck on what ever you decide to do.

---

### Post by andthewicked on 2010-07-30
thank you so much I thought there was somthing wrong with this file, I don't know how it got messed up but I'll take care of it and try this install agian thanks bro

---


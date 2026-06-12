---
title: "Can't activate Desktop Effects - nVidia/restricted modules?"
date: 2007-12-19
forum: Desktop Effects &amp; Customization
---

### Post by freymann on 2007-12-19
I have a  new ubuntu 7.10 system using a EVGA GeForce 8400 GS Video card with 256MB DDR2 memory.

I thought I'd see what all the neat desktop effects are about, but I can't make it work.

If I go to System > Administration > Restricted Drivers Manager, I get a dialog window that says:

You need to install the package
   linux-restricted-modules-2.6.22-14-server
for this program to work.

If I go to System > Synaptic Package Manager and search for "restricted" I see

-2.6.22.14.21 installed
-I also see 2.6.22-15-generic

and linux-restricted-modules-common
and linux-restricted-modules-generic

So it's there, but I can't activate it?

If I type compiz in a terminal window I get:

freymann@ubuntu:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

 In System -> Adminstration -> Screen and Graphics I see "nv" as the graphic driver. I cannot make it change to nVideo 8000 series.

compiz --replace comes up with the same output as above.

freymann@ubuntu:~$ dpkg -l | grep compiz
ii  compiz                                     1:0.6.2+git20071119-0ubuntu1~gutsy1 OpenGL window and compositing manager
ii  compiz-core                                1:0.6.2+git20071119-0ubuntu1~gutsy1 OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.6.0+git20071121-0ubuntu1~gutsy1   Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2          Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.6.2+git20071119-0ubuntu1~gutsy1 OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.6.2+git20071119-0ubuntu1~gutsy1 OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1          Compiz configuration settings manager
ii  emerald                                    0.3~git20070717-0ubuntu1            Decorator for compiz-fusion
ii  libcompizconfig-backend-gconf              0.5.2+git20071010-0ubuntu1          Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3          Settings library for plugins - OpenCompositi
ii  libemeraldengine0                          0.3~git20070717-0ubuntu1            Decoration engines for compiz-fusion
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1          Compiz configuration system bindings

---

### Post by oldos2er on 2007-12-19
> I have a  new ubuntu 7.10 system using a EVGA GeForce 8400 GS Video card with 256MB DDR2 memory.

I thought I'd see what all the neat desktop effects are about, but I can't make it work.

If I go to System > Administration > Restricted Drivers Manager, I get a dialog window that says:

You need to install the package
   linux-restricted-modules-2.6.22-14-server
for this program to work.

 Go into Software Sources and be sure you've checked off 'Source Code.'
Then type "sudo aptitude install     linux-restricted-modules-2.6.22-14-server" .

 Once installed, look in System, Preferences, Appearance, Visual Effects.

---

### Post by freymann on 2007-12-19
Nope, that didn't work either.

Sources was un-checked.

freymann@ubuntu:~$ sudo aptitude install linux-restricted-modules-2.6.22-14-server
[sudo] password for freymann:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find any package whose name or description matched "linux-restricted-modules-2.6.22-14-server"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done  

 I read somewhere that since it says xgl wasn't found, go install it, but when I search synaptic it says it's there.

 This is a brand new install. Seems strange. I don't *need* this to work, but it would be nice. Thanks for the reply though.

---

### Post by FuturePilot on 2007-12-19
> **freymann said:**
> Nope, that didn't work either.

Sources was un-checked.

freymann@ubuntu:~$ sudo aptitude install linux-restricted-modules-2.6.22-14-server
[sudo] password for freymann:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find any package whose name or description matched "linux-restricted-modules-2.6.22-14-server"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done  

 I read somewhere that since it says xgl wasn't found, go install it, but when I search synaptic it says it's there.

 This is a brand new install. Seems strange. I don't *need* this to work, but it would be nice. Thanks for the reply though.
Something could be wrong with your sources list. Could you post it?
```
cat /etc/apt/sources.list
```
Also you don't need XGL if you have a Nvidia card.

---

### Post by chips24 on 2007-12-20
reinstall it, thats what i do.

---

### Post by hhhhhx on 2007-12-20
I've been useing envy.  if you google 'dual monitors in ubuntu' there is a page about setting it up. It's a realy nice system but unfortunatly not open source

---

### Post by freymann on 2007-12-20
> **FuturePilot said:**
> Something could be wrong with your sources list. Could you post it?
```
cat /etc/apt/sources.list
```
Also you don't need XGL if you have a Nvidia card.

Ok, thanks.

Here's my contents of /etc/apt/sources.list

```

deb http://ubuntu.beryl-project.org feisty main
# 
# deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

I deleted automatix last night, but I see there were some lines at the bottom for it, so I just removed them.

I also installed beryl, but all I get is a white screen. Ctrl-Alt-ESC breaks me out of that.

---

### Post by freymann on 2007-12-20
In another similar thread, the user was asked to post the output of lspci. Here's mine!

```

00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0404 (rev a1)

```

 Maybe this is the cause of my no effects issue -- the last line says my device is Unknown. My video card is a EVGA GeForce 8400 GS with 256MB DDR2 memory with DVI, VGA, TV Out, etc.

 And other than not being able to get into the restricted drivers area, I guess I have to wait? or should I work on removing the restricted drivers and putting them back in? When I was in Synaptic Package Manager there were a ton of restricted driver entries, I would have no idea which to select for removal.

---

### Post by FuturePilot on 2007-12-20
```
**deb http://ubuntu.beryl-project.org feisty main**
# 
# deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

**deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted**
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
```
First 
```
gksudo gedit /etc/apt/sources.list
```
comment out the two lines in **Bold** by placing a # in front of the line.
Then run
```
sudo apt-get update
```
Also make sure the first 4 boxes are checked under System>Administration>Software Sources.

---

### Post by freymann on 2007-12-20
> **FuturePilot said:**
> 
**deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main**
**deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted**
First 
gksudo gedit /etc/apt/sources.list
comment out the two lines in **Bold** by placing a # in front of the line.
Then run
sudo apt-get update
Also make sure the first 4 boxes are checked under System>Administration>Software Sources.

 I rem'd out the two lines in bold, and there was a big paragraph that was duplicated so I removed one of those too.

 The sudo apt-get update did it's thing...

 Then in System>Admin>Software Sources, I had to check the 4th option, which did another update.

 However, I still get the same error when going to System>Admin>Restricted Drivers (need to install linux-restricted-modules-2.6.22-14-server).

 Visual Effects still can't be activated either. :-(

---


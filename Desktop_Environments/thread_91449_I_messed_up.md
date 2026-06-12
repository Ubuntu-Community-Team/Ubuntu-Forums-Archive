---
title: "I messed up"
date: 2005-11-17
forum: Desktop Environments
---

### Post by Jaakdedraak on 2005-11-17
I allways use the package manager to install or add new programs, but when i wanted to add a line to the reposatory,  i added a wrong one.
This causes Adept to crash everytime i start it up.
How can i delete that line in the sources.list?

cause when i try to edit sources.list i can't safe it because it's protected.
you see below here my sources.list with a wrong first line:






[http://www.safaribans.com/gpl/zsnes-cvs_cvs-20050927-1_i386.deb](http://www.safaribans.com/gpl/zsnes-cvs_cvs-20050927-1_i386.deb)
deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted 

## Uncomment the following two lines to fetch updated software from the network
deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy main restricted 
# deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy main restricted 

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-updates main restricted 
# deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy universe 
# deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy universe 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse 
# deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse 

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted 
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted 

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe 
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe 




thx for the help

---

### Post by bin on 2005-11-17
sudo kedit /etc/apt/sources.list
password

edit and save

---

### Post by Jaakdedraak on 2005-11-17
sudo: kedit: command not found :???: 

sorry i'm new to this

---

### Post by Suzan on 2005-11-17
"kedit" is just a text programm. If you use GNOME you haven't kedit (if you don't installed it manually). Use the program "gedit" instead:

sudo gedit /etc/apt/sources.list

---

### Post by rjwood on 2005-11-17
[quote=Jaakdedraak]sudo: kedit: command not found :???: 

sorry i'm new to this[/quote] 
Don't put the colin ( : )  in it. are you using ubuntu or kubuntu?

---

### Post by Jaakdedraak on 2005-11-17
i use kubuntu,

i looked up what text editor i have and it appears to be Kate

so when i use

jan@kamer18:~$ sudo kate /etc/apt/sources.list
Error: "/var/tmp/kdecache-jan" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"


i get this

---

### Post by bin on 2005-11-17
As this is the kubuntu forum I sort of assumed that OP is using kubuntu - sorry, I've just bolted kde on top of ubuntu and sort of assumed that it came with kedit by default in the Kubuntu install - sorry if it caused you any confusion Jaakdedraak;) 

I guess kwrite or kate would be standard??

in light

bin

---

### Post by Jaakdedraak on 2005-11-17
kwrite worked :) 

problem solved thx a lot you all

---


---
title: "No longer receiving updates"
date: 2006-09-22
forum: Desktop Environments
---

### Post by Leonivek on 2006-09-22
Sorry if this is posted elsewhere... I couldn't find anything recent about this problem... 

It seems that my system is no longer receiving updates.  I haven't received the latest kernel updates and a bunch of others.  I have Ubuntu installed at work also and I received a bunch of updates tonight that included the new kernel.  I came home, ran an update, but nothing.  I'm on kernel 2.6.15-26-386.  The new kernel is 2.6.15-27-386, I believe...

The thing is, I don't get any errors or problems when I run a **sudo apt-get update** or even through the "Update Manager" GUI.  :confused:  It tells me that my system is up to date when I know it isn't. :frown:

I've troubleshooted this to death without any clues whatsoever of what the problem may be.  ](*,)

Does anybody else have the same issue?  Does anyone know how I can fix this?

Thanks...

---

### Post by andypaxo on 2006-09-22
Not sure why you are not being notified of changes, do try this though:
```
sudo apt-get upgrade
```
This should install any new packages available.

For apt:
update = get new list of packages - like 'reload' in synaptic
upgrade = install newer versions of any out of date software

---

### Post by ubman on 2006-09-22
Yes  Same here still on firefox 1.5.05 no updates for awhile?

---

### Post by wieman01 on 2006-09-22
You could post the contents of "/etc/apt/sources.list"... perhaps there is a problem with the repositories.
> gedit /etc/apt/sources.list

---

### Post by ubman on 2006-09-22
Not sure why you are not being notified of changes, do try this though:
Code:

sudo apt-get upgrade

This should install any new packages available.

For apt:
update = get new list of packages - like 'reload' in synaptic
upgrade = install newer versions of any out of date software




Tried this too no go?

---

### Post by ubman on 2006-09-22
> **wieman01 said:**
> You could post the contents of "/etc/apt/sources.list"... perhaps there is a problem with the repositories.


deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) dapper main #Ntfs Driver
deb-src [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) dapper main #Ntfs Driver
# deb [http://kubuntu.org/packages/kde-354/](http://kubuntu.org/packages/kde-354/) dapper main Reply With Quote

---

### Post by samkon on 2006-09-22
to reach all packets you should replace your /etc/apt/sources.list as below;

> wget [http://ubuntu-tr.com/download/sources.list](http://ubuntu-tr.com/download/sources.list)

sudo cp sources.list /etc/apt/sources.list

sudo apt-get update

---

### Post by Leonivek on 2006-09-22
> **wieman01 said:**
> You could post the contents of "/etc/apt/sources.list"... perhaps there is a problem with the repositories.

I've checked this also and it all seems fine, but here it is:
```
deb http://packages.freecontrib.org/plf/ dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

## Automatix sources.list
## This is automatically generated by Automatix
####################################
### Official Ubuntu Repositories ###
# Dapper Final Release Repository
deb-src http://archive.ubuntu.com/ubuntu dapper main
deb-src http://archive.ubuntu.com/ubuntu dapper restricted
deb-src http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse
# Dapper Security Updates
# deb http://archive.ubuntu.com/ubuntu dapper-security main
deb-src http://archive.ubuntu.com/ubuntu dapper-security main
# deb http://archive.ubuntu.com/ubuntu dapper-security restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-security restricted
# deb http://archive.ubuntu.com/ubuntu dapper-security universe
deb-src http://archive.ubuntu.com/ubuntu dapper-security universe
# deb http://archive.ubuntu.com/ubuntu dapper-security multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-security multiverse
# Dapper Bugfix Updates
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main
deb-src http://archive.ubuntu.com/ubuntu dapper-updates restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe
deb-src http://archive.ubuntu.com/ubuntu dapper-updates multiverse
# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
# deb http://archive.ubuntu.com/ubuntu dapper-backports main
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main
# deb http://archive.ubuntu.com/ubuntu dapper-backports restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-backports restricted
# deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb http://archive.ubuntu.com/ubuntu dapper-backports universe
deb-src http://archive.ubuntu.com/ubuntu dapper-backports universe
# deb http://archive.ubuntu.com/ubuntu dapper-backports multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports multiverse
deb http://archive.canonical.com/ubuntu dapper-commercial main
##############################
### Automatix Repositories ###
deb http://www.getautomatix.com/apt dapper main
## created by automatixrepo3
###   USER-ADDED SOURCES   ###
# MOBLOCK
deb http://moblock-deb.sourceforge.net/debian unstable main
deb-src http://moblock-deb.sourceforge.net/debian unstable main
# WINE
deb http://wine.lowvoice.nl/apt dapper main
deb http://dl.google.com/linux/deb/ stable non-free
deb http://www.getautomatix.com/apt kubuntu main
deb http://archive.ubuntu.com/ubuntu/ dapper multiverse universe restricted main
deb http://ubuntu.compiz.net/ dapper main
deb http://www.beerorkid.com/compiz/ dapper main
deb http://theli.free.fr/packages/ dapper listen
deb http://people.ubuntu.com/~seb128/deb ./
```

Thanks!

---

### Post by samkon on 2006-09-22
> **samkon said:**
> to reach all packets you should replace your /etc/apt/sources.list as below;

but I don't know that sources list should be different for different countries. You should be sure about it that you will not have any problems about language. Let you control tle sources.list that I prefer to you above first..

good luck..

---

### Post by samkon on 2006-09-22
I don't know that sources list should be different for different countries. You should be sure about it that you will not have any problems about language. Let you control tle sources.list that I prefer to you below first..

you should replace your /etc/apt/souces.list as below;

```

wget http://ubuntu-tr.com/download/sources.list

sudo cp sources.list /etc/apt/sources.list

sudo apt-get update

```
good luck..

---

### Post by ubman on 2006-09-22
> **samkon said:**
> to reach all packets you should replace your /etc/apt/sources.list as below;



This got me a nvidia kernel update only still on firefox 1.5.05 there should be a flash update also i belive?

---

### Post by wieman01 on 2006-09-22
Do you get error messages when you fire up "Synaptic Package Manager"?

---

### Post by Leonivek on 2006-09-22
> **wieman01 said:**
> Do you get error messages when you fire up "Synaptic Package Manager"?

Nope.  Nothing.  Everything seems normal. :cool: If I didn't already know about the updates, I would never suspect there was something wrong with my updates.

I'm confused. :confused:

---

### Post by Leonivek on 2006-09-22
> **ubman said:**
>  *<snip>* there should be a flash update also i believe?

Yes!  That too, now that you mention it.  Didn't get that one either when I did get it a work (with an error, though... that's another thread).

Firefox, too... that's if they have the new version for Ubuntu in the repos...

---

### Post by wieman01 on 2006-09-22
Leonivek, not sure how this has happened but something is wrong with your sources file. All the program updates are uncommented:

_Example:_
> # deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted

Remove the # in front of each line and your updates should be there once you fire up the "update manager"...

Your sources file needs serious overhaul, man. Try this link later on:

[http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")

---

### Post by wieman01 on 2006-09-22
The "src" updates are there, but not the updates for the packages. That's your problem. No surprise!

**EDIT:**
This is the right path for "Ubuntu supported packages":
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
To edit the sources file from a terminal window:
> sudo gedit /etc/apt/sources.list

---

### Post by Leonivek on 2006-09-22
> **wieman01 said:**
> The "src" updates are there, but not the updates for the packages. That's your problem. No surprise!

**EDIT:**
This is the right path for "Ubuntu supported packages":

To edit the sources file from a terminal window:

OMG... The funny thing is, I knew this!  There was a reason I commented them out, but I don't remember why... I must have been troubleshooting something else and forgot to uncomment them!  I'm so stupid.  Even when I was troubleshooting this problem, I checked my sources and didn't notice or even remember!

Thanks!

---

### Post by wieman01 on 2006-09-22
> **Leonivek said:**
> OMG... The funny thing is, I knew this!  There was a reason I commented them out, but I don't remember why... I must have been troubleshooting something else and forgot to uncomment them!  I'm so stupid.  Even when I was troubleshooting this problem, I checked my sources and didn't notice or even remember!
Haha... Lesson learned. Sometimes solutions are so obvious you don't see the wood for the trees. Nice talking to you anyway. :-)

---

### Post by samkon on 2006-09-22
> **ubman said:**
> This got me a nvidia kernel update only still on firefox 1.5.05 there should be a flash update also i belive?

I did not understand what you mean. if the sources list that I prefered to yu gets you to a update, isn't it mean that works? if you run tihese commands, you will reach all packets, and will not have any problem without if there may be a language problem beacouse I took this sources list from a Turkish site which helps to ubuntu users as here in Turkey.

```

wget http://ubuntu-tr.com/download/sources.list

sudo cp sources.list /etc/apt/sources.list

sudo apt-get update
```

I hope it ok. good luck..

---

### Post by Leonivek on 2006-09-22
> **wieman01 said:**
> Haha... Lesson learned. Sometimes solutions are so obvious you don't see the wood for the trees. Nice talking to you anyway. :-)

Thanks... you too!  :)

---


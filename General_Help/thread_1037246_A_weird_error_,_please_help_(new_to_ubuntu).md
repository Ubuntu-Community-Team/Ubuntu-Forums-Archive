---
title: "A weird error , please help (new to ubuntu)"
date: 2009-01-11
forum: General Help
---

### Post by snarf103 on 2009-01-11
I might've killed my ubuntu, please help me :confused:

When i try the add/remove thing to get new programs i get this:

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

And when i try use the synaptic to check the permissions etc i get this:

E: Type 'v' is not known on line 60 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

Please help me out  ,i cant install anything

by the way , it ****ed up when i was trying to install this: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)  maybe that'll show which files i need to repair?

---

### Post by _sleeper on 2009-01-11
do:
```

cat /etc/apt/sources.lst

```

and post it here to see if there's something wrong with your sources list.

also you could try on terminal:

```

dpkg --configure -a

```

in case there are broken packages.

---

### Post by taurus on 2009-01-11
There is something with line 60 in your /etc/apt/sources.list.  You need to fix it before you can update or upgrade your machine.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by snarf103 on 2009-01-11
> **taurus said:**
> There is something with line 60 in your /etc/apt/sources.list.  You need to fix it before you can update or upgrade your machine.

```
gksudo gksudo /etc/apt/sources.list
```

Sorry, im new, so where do i enter : ```
gksudo gksudo /etc/apt/sources.list
``` ?

---

### Post by _sleeper on 2009-01-11
open a terminal and type it there!
and do not type

```
gksu gksu /etc/apt/sources.lst

```

but ```

gksu gedit /etc/apt/sources.lst
```

the buddy corrected the command!

---

### Post by taurus on 2009-01-11
Just open a terminal and run that command from it.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
It's probably the repo (wine) that you've added earlier.  If you are not sure which line, just post the whole content of your /etc/apt/sources.list here and somebody will point it out for you.

---

### Post by snarf103 on 2009-01-12
ok, so i did it and i got this:

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security restricted main multiverse universe
v



Can anyone tell me what to do with this? (it says i dont have the rights or something like that to change it )

---

### Post by snarf103 on 2009-01-12
Cant anyone tell me what to do, i know its my own fault, but with that list not working i cant do anything :(

---

### Post by taurus on 2009-01-12
There is a **[COLOR="Red"]v[/COLOR]** on the last line.  Remove it.

---

### Post by snarf103 on 2009-01-12
Yeah i was trying that, but i cant seeing as it says i cant save it because i dont have the administrative rights , while im the only account on ubuntu :/

---

### Post by taurus on 2009-01-12
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by snarf103 on 2009-01-12
Thanks man, my updates and stuff are running again, any tips on how to install wine in a alternative way?

---

### Post by taurus on 2009-01-12
Run these commands from a terminal.

```

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/winehq.list
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install wine
winecfg
```

---


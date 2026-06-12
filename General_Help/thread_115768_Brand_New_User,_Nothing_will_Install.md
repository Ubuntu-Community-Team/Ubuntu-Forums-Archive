---
title: "Brand New User, Nothing will Install"
date: 2006-01-11
forum: General Help
---

### Post by manuzza on 2006-01-11
Okay so I have installed Kubuntu on my laptop for the first time (previously had Gentoo). I am trying to install some apps I need. this is urgent coz' if I don't get it done soon I will have no laptop at work tomorrow!

So far I have:

Added universe
Done an apt-get update (the count of packages in adept went from 1300 or so to 15000 or so, so it worked).
Searched Adept for these packages (ie, lots of firefox plugins etc, but none of the apps themselves)
Executed apt-get install mozill-firefox mozilla-thunderbird gimp (reported as having to installation candidate)

PLEASE: how do I find and install basic applications?!?

---

### Post by feathers on 2006-01-11
Could you please send your /etc/sources.list so we can see what you have got.

---

### Post by manuzza on 2006-01-11
I hope you mean /etc/apt/sources.list ... 

deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


```
## Uncomment the following two lines to fetch updated software from the network
# deb http://au.archive.ubuntu.com/ubuntu breezy main restricted
# deb-src http://au.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb http://au.archive.ubuntu.com/ubuntu breezy-updates main restricted
# deb-src http://au.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu breezy universe
deb-src http://au.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

# deb http://security.ubuntu.com/ubuntu breezy-security main restricted
# deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```

---

### Post by feathers on 2006-01-11
Now you have ONLY multiverse. Use this line: 
## Uncomment the following two lines to fetch updated software from the network
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse

If it works, ou schould add breezy security as well.

---

### Post by PsychoTrauma on 2006-01-11
[QUOTE=manuzza]Okay so I have installed Kubuntu on my laptop for the first time (previously had Gentoo). I am trying to install some apps I need. this is urgent coz' if I don't get it done soon I will have no laptop at work tomorrow!

So far I have:

Added universe
Done an apt-get update (the count of packages in adept went from 1300 or so to 15000 or so, so it worked).
Searched Adept for these packages (ie, lots of firefox plugins etc, but none of the apps themselves)
Executed apt-get install mozill-firefox mozilla-thunderbird gimp (reported as having to installation candidate)

PLEASE: how do I find and install basic applications?!?[/QUOTE]

uncomment: (remove the # from the beginning)

```
deb http://au.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://au.archive.ubuntu.com/ubuntu breezy main restricted

deb http://au.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu breezy-updates main restricted

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```

open up konsole and do:

```
sudo apt-get install mozilla-firefox mozilla-thunderbird gimp
```

---

### Post by manuzza on 2006-01-11
[QUOTE=feathers]Now you have ONLY multiverse. Use this line: 
## Uncomment the following two lines to fetch updated software from the network
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse

If it works, ou schould add breezy security as well.[/QUOTE]

Okay, so NOW after apt-get available packages have increased from 14500 to 17300, and mozilla-firefox mozilla-thunderbird and gimp are suddenly available.

Just so I learn from this, how did this happen? Some doco I read told me to uncomment those lines to get universe up, but I never commented out anything else. What exactly did those extra two lines add?

Thanks for your very quick help...

---

### Post by feathers on 2006-01-11
Kubuntu or ubuntu packages are sorted according to this scheme: 
main: All the packages that belong to the basic system, probably the ones on the cd. I am not sure though. 
restricted: All packages that have restrictions such as licence, etc. They are not free as in free software. 
universe: A lot of other programs that are not in the main system. I think they are not as extensively tested. 
multiverse: Even more packages. 
Now, if you only use the multiverse repository, you only get packages from that one. So usually you have "main" in the least, then "restricted" if you are not a follower of the one true creed of free software, then you can add more packages with "mulitverse" and "universe". This means you have basically the same software basis as in Debian.

---


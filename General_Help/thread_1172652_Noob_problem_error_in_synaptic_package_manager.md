---
title: "Noob problem: error in synaptic package manager"
date: 2009-05-28
forum: General Help
---

### Post by rakspsp on 2009-05-28
i have ubuntu. I recently added several applications and 3rd party site in repository, i also tried installing some application but i was not sucessful. now i get this message when i open synaptic package manager


E: Type '“deb' is not known on line 58 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

and i cannot continue using it. . please help.

thank you.

---

### Post by merlinus on 2009-05-28
You might try this in a terminal to refresh the repos:

```

sudo apt-get update

```and then run synaptic again.

---

### Post by 73ckn797 on 2009-05-28
> **rakspsp said:**
> i have ubuntu. I recently added several applications and 3rd party site in repository, i also tried installing some application but i was not sucessful. now i get this message when i open synaptic package manager


E: Type '“deb' is not known on line 58 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

and i cannot continue using it. . please help.

thank you.


What is the exact reading of the line 58.

---

### Post by ntowakbh on 2009-05-28
> **rakspsp said:**
> i have ubuntu. I recently added several applications and 3rd party site in repository, i also tried installing some application but i was not sucessful. now i get this message when i open synaptic package manager


E: Type '“deb' is not known on line 58 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

and i cannot continue using it. . please help.

thank you.

Can you paste the results of
Applications --> Acessories --> Terminal
```
cat /etc/apt/sources.list
```
in this topic?

---

### Post by michy99 on 2009-05-28
> **rakspsp said:**
> i have ubuntu. I recently added several applications and 3rd party site in repository, i also tried installing some application but i was not sucessful. now i get this message when i open synaptic package manager


E: Type '“deb' is not known on line 58 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

and i cannot continue using it. . please help.

thank you.

It looks like you have a quotation mark (") before the word 'deb' on line 58. Open up the file as root.```
gksudo gedit /etc/apt/sources.list
```

Find the offending quotation mark on line 58, remove it, and save. Should fix it.

---

### Post by rakspsp on 2009-05-29
> **ntowakbh said:**
> Can you paste the results of
Applications --> Acessories --> Terminal
```
cat /etc/apt/sources.list
```in this topic?


This is what was generated. thank you.

main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

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
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main”
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main”
rakshit@ubuntu:~$

---

### Post by rakspsp on 2009-05-29
got it guys.. solved the problem. it was the " beforethe deb. thanks for the sol.

---

### Post by Soul-Sing on 2009-05-29
Automatix? :( That force -yes script.....?)

---


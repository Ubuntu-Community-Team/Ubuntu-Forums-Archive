---
title: "help with repositories"
date: 2006-03-12
forum: Desktop Environments
---

### Post by mexgirl87 on 2006-03-12
Hello, im a new user in linux, im currently using ubuntu 5.10,  i bearly installed it to my computer and im having some problem with the repositories because everytime i go and open the synaptic package manager it comes up with a screen that says

E: Type 'ded' is not known on line 38 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

i have no clue on what to do to fix  this could somebody please help me. thank  you realy appreciate it.

---

### Post by eriefisher on 2006-03-12
Open a termial and type-sudo gedit /etc/apt/sources.list

Post the out put here.

eriefisher

---

### Post by mexgirl87 on 2006-03-12
ok i did that so heres what came out 
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe main restricted multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe


ded http:// archive.ubuntu.com/ubuntu breezy-backports main universe multiverse restricted
deb http:// archive.ubuntu.com.ubuntu breezy-backports main universe multiverse restricted

---

### Post by eriefisher on 2006-03-12
The second "deb" up from the bottom accually says "ded". Change the "d" to a "b" and try again.

eriefisher

---

### Post by mexgirl87 on 2006-03-12
ok i changed it then i saved  it then i went back and opend the synaptic package manager and this is what came out

W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http: archive.ubuntu.com/ubuntu/breezy-backports Packages (/var/lib/apt/lists/dists_archive.ubuntu.com_ubuntu_breezy-backports_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http: archive.ubuntu.com/ubuntu/main Packages (/var/lib/apt/lists/dists_archive.ubuntu.com_ubuntu_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http: archive.ubuntu.com/ubuntu/universe Packages (/var/lib/apt/lists/dists_archive.ubuntu.com_ubuntu_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http: archive.ubuntu.com/ubuntu/multiverse Packages (/var/lib/apt/lists/dists_archive.ubuntu.com_ubuntu_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http: archive.ubuntu.com/ubuntu/restricted Packages (/var/lib/apt/lists/dists_archive.ubuntu.com_ubuntu_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http: archive.ubuntu.com.ubuntu/breezy-backports Packages (/var/lib/apt/lists/dists_archive.ubuntu.com.ubuntu_breezy-backports_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http: archive.ubuntu.com.ubuntu/main Packages (/var/lib/apt/lists/dists_archive.ubuntu.com.ubuntu_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http: archive.ubuntu.com.ubuntu/universe Packages (/var/lib/apt/lists/dists_archive.ubuntu.com.ubuntu_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http: archive.ubuntu.com.ubuntu/multiverse Packages (/var/lib/apt/lists/dists_archive.ubuntu.com.ubuntu_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http: archive.ubuntu.com.ubuntu/restricted Packages (/var/lib/apt/lists/dists_archive.ubuntu.com.ubuntu_restricted_binary-i386_Packages) - stat (2 No such file or directory)

so what do you think i should do know? thanks

---

### Post by eriefisher on 2006-03-12
This looks like a problem with a connection or the repo is down or to busy at the moment. Maybe give it some time and try again unless someone else is having the same problem. I'm not at my box right now so I can't verify that but I would retry.

eriefisher

---

### Post by mexgirl87 on 2006-03-12
ok cuz i did the updates cuz it came out that i had new updates so i installed those and they installed right  so know im going to restart my computer see if that helps out in my computer. thanks

---

### Post by mexgirl87 on 2006-03-12
thanks for all of your help i think it works now because now i could all add applications. thanks again.

---

### Post by eriefisher on 2006-03-12
Before you play around with your sources.list you should back them up first.

In a terminal type:mv /etc/apt/sources.list /etc/apt/sources.list_backup

This way you could restore it should something go wrong. You should do this with any file before you edit it just to be safe.

eriefisher

---

### Post by mexgirl87 on 2006-03-12
I think I already messed up my computer already, cuz now i cant log in to ubuntu, is thier any way that i could probably just uninstall it and take of the particion that i made in my computer. well thanks for your help really appreciate it.

---

### Post by WildTangent on 2006-03-12
Remember whenever you make changes to your sources.list to update your repo list in apt:
```
sudo apt-get update
```

-Wild

---

### Post by mexgirl87 on 2006-03-12
were do i go and type that code in?

---

### Post by Adrian on 2006-03-12
[QUOTE=mexgirl87]were do i go and type that code in?[/QUOTE]

In a terminal. You can find one in the Applications menu.

Applications > Accessories > Terminal

---

### Post by eriefisher on 2006-03-12
> [QUOTE=mexgirl87]I think I already messed up my computer already, cuz now i cant log in to ubuntu, is thier any way that i could probably just uninstall it and take of the particion that i made in my computer. well thanks for your help really appreciate it.[/QUOTE]

What is happening exactly. Where are you getting stuck.

eriefisher

---

### Post by mexgirl87 on 2006-03-12
[QUOTE=eriefisher]What is happening exactly. Where are you getting stuck.

eriefisher[/QUOTE]

well what happens is that when i turn on my computer and i put my username and password it dosent want to connect , a message that says 

GMD could not write to your authorization file.  This could mean that you are out of disk space or that your home directory could not be opened for writing.  In any case, it is not possible to log in.  Please contact your system administrator

this is what is confussing me because now i dont know whats going on with my ubuntu. hopefully you could help me thanks

---

### Post by eriefisher on 2006-03-12
Can you get on in failsafe mode?

eriefisher

---

### Post by mexgirl87 on 2006-03-12
i went into the recovery mode and it asks for root@ubuntu:~#

what should i put in thier?

---

### Post by eriefisher on 2006-03-12
It looks like you permissions are screwed up somehow. I'm not sure how to correct that from here, my kung fu is not that good yet but hang tight I'm sure the answer is here with someone with more experience.

eriefisher

---

### Post by mexgirl87 on 2006-03-12
ok thanks

---


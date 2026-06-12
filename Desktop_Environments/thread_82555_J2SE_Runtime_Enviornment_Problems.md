---
title: "J2SE Runtime Enviornment Problems"
date: 2005-10-26
forum: Desktop Environments
---

### Post by pacoo2454 on 2005-10-26
im having some problems getting the j2se runtime enviornment installed onto my machine, i looked it up on ubuntuguide.org and did everything it told me, changing the repositories and what not then i went into the terminal and did - 

sudo apt-get install sun-j2re1.5

and it gave me this 

Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package sun-j2re1.5

im still a noob when it comes to linux and i dont know what it means, if someone could help me that would be great, here is my sources.list file just incase you need to look at it to help

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted



thank you 

jeff

---

### Post by gillion on 2005-10-26
[FONT="Arial"][SIZE="6"]THE UBUNTU BACKPORTS REPOSITORY ARE NOT YET ACTIVE FOR BREEZY AS THE NEW DISTRO (6.04 dapper drake) HAS NOT BEGUN WORK YET ![/SIZE][/FONT]

---

### Post by Moonbuzz on 2005-10-26
So what is it exactly you're saying? :D

---

### Post by coldrick on 2005-10-26
At this stage, you might want to install it yourself - given that the backports repository appears not yet to be available :) 

The instructions on [my blog]("http://blogs.sun.com/roller/page/coldrick?entry=java_development_on_ubuntu_part") are for the jdk, but will work fine for the jre.

Regards,
David

---

### Post by RAOF on 2005-10-26
Or even better, follow this [howto]("http://www.ubuntuforums.org/showthread.php?t=76735&highlight=java+1.5+plugin").

Also, you'll need to fix your sources.list:  All those "hoary"s should be "breezy"s, and you should remove the backports - the breezy backports don't exist yet.

---

### Post by racecat on 2005-10-26
There seems to be a bit of confusion. If your sources.list say "hoary" as posted, you are probably using rel. 5.04 "Hoary Hedgehog". This being the rel. 5.10 "Breezy" forum has probably caused said confusion.

Anyway, in hoary, the mirrormax repositories for backports were unofficial and unsupported, however they were recently closed down and moved to the official repositories. Replace the backports section with:


## Backports
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main restricted universe multiverse


Hope this helps

---

### Post by pacoo2454 on 2005-10-27
hey
sorry about the confusion, my mistake
but thank you racecat for the help
once again, sorry for posting in the wrong forum

---


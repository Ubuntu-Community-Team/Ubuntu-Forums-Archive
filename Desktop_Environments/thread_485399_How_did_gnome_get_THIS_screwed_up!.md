---
title: "How did gnome get THIS screwed up?!"
date: 2007-06-26
forum: Desktop Environments
---

### Post by wilberfan on 2007-06-26
Somehow, someway, my gnome (Ubuntu) install seems to have come completely apart at the seams!!  The XFCE desktop still works, but gnome doesn't even show up on the login screen!

And how the heck can THIS happen?!:

> wilberfan@dell-feisty:~$ sudo apt-get --reinstall install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: alacarte but it is not going to be installed
                  Depends: gnome-applets but it is not going to be installed
                  Depends: gnome-control-center but it is not going to be installed
                  Depends: gnome-panel but it is not going to be installed
                  Depends: gnome-session but it is not going to be installed
                  Depends: gnome-terminal but it is not going to be installed
                  Depends: nautilus but it is not going to be installed
                  Depends: nautilus-cd-burner but it is not going to be installed
                  Depends: nautilus-sendto but it is not going to be installed
                  Recommends: bug-buddy but it is not going to be installed
                  Recommends: contact-lookup-applet but it is not going to be installed
                  Recommends: deskbar-applet but it is not going to be installed
                  Recommends: ekiga but it is not going to be installed
                  Recommends: evolution but it is not going to be installed
                  Recommends: evolution-exchange but it is not going to be installed
                  Recommends: evolution-plugins but it is not going to be installed
                  Recommends: gaim but it is not going to be installed
E: Broken packages

Is there a (relatively) fix to this?!     Any idea what happened?!

---

### Post by divague on 2007-06-26
maybe this

$sudo apt-get install -f

---

### Post by wilberfan on 2007-06-26
> **divague said:**
> maybe this

$sudo apt-get install -f

> wilberfan@dell-feisty:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

:(

---

### Post by joe.turion64x2 on 2007-06-26
Is reinstalling an option? Perhaps it is faster.

---

### Post by gbesso on 2007-06-26
Post your /etc/apt/sources.list file please ;)

---

### Post by wilberfan on 2007-06-26
> **gbesso said:**
> Post your /etc/apt/sources.list file please ;)

> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse

## alltray repository
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) edgy main dupdate french
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu main dupdate french
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
#AUTOMATIX REPOS END

#FONT REPOS
deb [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts
deb-src [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts
#END OF FONT REPOS
deb [http://www.museek-plus.org/ubuntu](http://www.museek-plus.org/ubuntu) feisty main
deb [http://gnomefreak.youmortals.com/mozilla-testing](http://gnomefreak.youmortals.com/mozilla-testing) feisty main


Re-installing is, of course, an option...   but it's a pain-in-the-A option....

---

### Post by gbesso on 2007-06-26
I'm afraid I can't see anything major in there, you could try removing all non-official ubuntu repositories and try again.

On another note, you might want to try
```
sudo aptitude install gnome-desktop
```
It should offer a solution in case of dependency problems which is possibly what you have.

P.S 
In case you decide to reinstall, you might want to back up your home folder/partition, most of your settings are stored there and should work on a newly installed system as long as the packages are reinstalled.

Sorry I couldn't have been more helpful.

---

### Post by wilberfan on 2007-06-26
Duuuuuuuuude!

"sudo aptitude install gnome-desktop" didn't work...but "sudo aptitude install gnome-desktop-environment" DID!  :p

This all took place on my backup box, so I'll have to keep an eye on how well things run from this point...   A re-install wouldn't be the end of the world...

ANY idea how gnome got so corrupted in the first place?!

---

### Post by kevinlyfellow on 2007-06-27
Some people believe automatix is buggy and dangerous, so it may be that.  What have you used automatix for?

Does your computer have the these things installed already?  How about when you try to reinstall a single application, like `sudo apt-get --reinstall install alacarte`?  You may be able to use synaptic to better understand what's going on.

You could also try and remove the ubuntu-desktop and then install it.

---

### Post by wilberfan on 2007-06-27
> **kevinlyfellow said:**
> Some people believe automatix is buggy and dangerous, so it may be that.  What have you used automatix for?

Erm...probably swiftfox and it's plugins?   It's been awhile, don't remember exactly...  I've seen both praise and horror regarding Automatix...

> Does your computer have the these things installed already?  How about when you try to reinstall a single application, like `sudo apt-get --reinstall install alacarte`?  You may be able to use synaptic to better understand what's going on.

I just tried a reinstall of alacarte, and it seemed to go okay...

> You could also try and remove the ubuntu-desktop and then install it.

Actually, I did a "sudo apt-get install ubuntu-desktop" right after the gnome-desktop-environment install seemed to go well...  

Things have been screwey for a few days, actually...   My Update Manager has been telling me that, "Not all updates can be installed--run a partial upgrade", etc...   (In fact, it's still giving me that message...)  Wonder if that's a repo conflict, or...?

[edit]  I removed from of the other repos, and the Update Manager told me that my system was up-to-date...and that "not all updates can be installed" message did NOT appear any more...

---

### Post by kevinlyfellow on 2007-06-27
> **wilberfan said:**
> 
Things have been screwey for a few days, actually...   My Update Manager has been telling me that, "Not all updates can be installed--run a partial upgrade", etc...   (In fact, it's still giving me that message...)  Wonder if that's a repo conflict, or...?

I've come across problems with repo conflicts every once and a while, and it really does seem like thats what's going on.  Perhaps trying something like `dpkg-query -l | less` and look at some of the versions installed.  officially supported packages will have "ubuntu" in the version number.  If something like alacarte or gnome-terminal aren't the official versions, then it looks like you have some problems to resolve.

Also, you can try to disable non ubuntu hosted repos.  If that gets the update manager to go away, then you can find the offending repo.

---


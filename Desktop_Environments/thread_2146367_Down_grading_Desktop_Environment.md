---
title: "Down grading Desktop Environment"
date: 2013-05-18
forum: Desktop Environments
---

### Post by WinterMadness on 2013-05-18
(Please dont be turned away if you arent familiar with KDE, this can all be done via the command line, I just need to be told what to do, this can apply to any ubuntu software!)

I followed the following guide to install the latest version of KDE on my system: [http://www.noobslab.com/2013/02/install-kde-410-in-ubuntu-12101204linux.html](http://www.noobslab.com/2013/02/install-kde-410-in-ubuntu-12101204linux.html)

I quickly realized that this version of KDE is simply not meant for the version of Ubuntu that I have(Ubuntu 12.04.2 LTS), and eventually, I need to do something about that. But for the time being, I need to undo what was done here and get my old version of KDE back.

So what I'm thinking I need to do is uninstall KDE, remove the repository of the latest version of KDE, and reinstall KDE from the official repository. The problem is I dont know how to do that, because I dont know what im looking at in my source list

Here are the commands I entered to be able to install the newest KDE

sudo add-apt-repository ppa:kubuntu-ppa/backports
sudo apt-get update
sudo apt-get dist-upgrade

heres my sources.list. Maybe I can simply remove something here?

# deb cdrom:[Kubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120423)]/ dists/precise/main/binary-i386/

# deb cdrom:[Kubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120423)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Kubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120423)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free

---

### Post by WinterMadness on 2013-05-18
(Please dont be turned away if you arent familiar with KDE, this can all be done via the command line, I just need to be told what to do, this can apply to any ubuntu software!)

I followed the following guide to install the latest version of KDE on my system: [http://www.noobslab.com/2013/02/inst...1204linux.html](http://www.noobslab.com/2013/02/inst...1204linux.html)

I quickly realized that this version of KDE is simply not meant for the version of Ubuntu that I have(Ubuntu 12.04.2 LTS), and eventually, I need to do something about that. But for the time being, I need to undo what was done here and get my old version of KDE back.

**So what I'm thinking I need to do is uninstall KDE, remove the repository of the latest version of KDE, and reinstall KDE from the official repository**. The problem is I dont know how to do that, because I dont know what im looking at in my source list

Here are the commands I entered to be able to install the newest KDE

sudo add-apt-repository ppa:kubuntu-ppa/backports
sudo apt-get update
sudo apt-get dist-upgrade

heres my sources.list. Maybe I can simply remove something here?

# deb cdrom:[Kubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120423)]/ dists/precise/main/binary-i386/

# deb cdrom:[Kubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120423)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Kubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120423)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free

---

### Post by CatKiller on 2013-05-18
You don't need to uninstall KDE, just force the version to a lower one. You can do it all in Synaptic, although there are command-line equivalents.

The repository that you added is probably in sources.lst.d.

---

### Post by WinterMadness on 2013-05-18
> **CatKiller said:**
> You don't need to uninstall KDE, just force the version to a lower one. You can do it all in Synaptic, although there are command-line equivalents.

The repository that you added is probably in sources.lst.d.

What are the command line equivalents?

---

### Post by CatKiller on 2013-05-18
apt-get --force-version something something. Have a look in the man page. I'm on my phone, so I can't really check for you.

Aptitude is a good command-line option too, although I don't think it's installed by default any more. You can give it apt-get style commands, or just invoke it for the same kind of thing as Synaptic, but on the command line.

---

### Post by Frogs Hair on 2013-05-18
You can force package versions in the synaptic package manager by viewing versions under properties. This is a long process and it may be quicker to backup and re-install. Using aptitude (not apt) from the command line would require knowing the package names and chances are the are many. Investigating a PPA purge may be useful as well.

---

### Post by Cheesemill on 2013-05-18
You can use ppa-purge to do it all for you.
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:kubuntu-ppa/backports
```

This will remove the KDE PPA you added and revert all of the updated packages back to the versions in the standard repositories.

---

### Post by coffeecat on 2013-05-18
Threads merged. Please do not post duplicates in different parts of the forum.

---

### Post by WinterMadness on 2013-05-18
> **Cheesemill said:**
> You can use ppa-purge to do it all for you.
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:kubuntu-ppa/backports
```

This will remove the KDE PPA you added and revert all of the updated packages back to the versions in the standard repositories.

I did that, now when I start the computer it drops to terminal. I try to type kstart and it says cannot connect to x server.

---


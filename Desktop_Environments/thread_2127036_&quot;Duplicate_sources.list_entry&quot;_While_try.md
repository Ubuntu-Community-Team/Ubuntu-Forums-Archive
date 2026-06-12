---
title: "&quot;Duplicate sources.list entry&quot; While trying to install third party themes"
date: 2013-03-18
forum: Desktop Environments
---

### Post by poignantprick on 2013-03-18
This is my second issue with the source list tonight. I don't really understand it. I was just trying to install a some third party themes for Gnome when I ran into this issue:

W: Duplicate sources.list entry [http://archive.canonical.com/](http://archive.canonical.com/) precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.canonical.com/](http://archive.canonical.com/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

I did what was suggested above. Didn't help.

I'm going to post the source list, but I don't know how to put it into a window that scrolls. If someone could instruct me on how to do so I will edit, or learn for the next time. I don't know much, but I am a pretty quick study. And I'd like to make it as easy as possible for you to helo me :)

Thanks!

Here is the source list:

```
# deb cdrom:[Xubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ dists/precise/main/binary-i386/

# deb cdrom:[Xubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ dists/precise/multiverse/binary-i386/
# deb cdrom:[Xubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Xubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ dists/precise/universe/binary-i386/
# deb cdrom:[Xubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ precise main multiverse restricted universe

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
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
```

---

### Post by ibjsb4 on 2013-03-18
Thought you got this fixed earlier.  Nomatter

The last two lines need to be removed

deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner 						

Or you can just comment them out

#deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
#deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner

---

### Post by poignantprick on 2013-03-19
Earlier it was that there was not a space before "precise" on the bottom two lines. So, I had a really similar issue dealing with those same two lines. The problem manifested differently though. Sorry to be redundent. 

Thanks again!

---


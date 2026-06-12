---
title: "X11VNC &quot;unable to fetch some archives&quot;"
date: 2012-01-07
forum: Desktop Environments
---

### Post by skyshrine on 2012-01-07
I'm sure this is a very noob question.  But I need help installing x11vnc.  I've successfully done it on several servers, but one particular machine has an older copy of Ubuntu, and when I do this:

sudo apt-get install x11vnc

I get this:

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libvncserver0
Suggested packages:
  libvncserver0-dbg
The following NEW packages will be installed:
  libvncserver0 x11vnc
0 upgraded, 2 newly installed, 0 to remove and 259 not upgraded.
Need to get 933kB of archives.
After this operation, 2,015kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libvncserver0 x11vnc
Install these packages without verification [y/N]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main libvncserver0 0.9.3.dfsg.1-1ubuntu2
  404  Not Found [IP: 91.189.92.182 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe x11vnc 0.9.3.dfsg.1-1ubuntu2
  404  Not Found [IP: 91.189.92.182 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libv/libvncserver/libvncserver0_0.9.3.dfsg.1-1ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libv/libvncserver/libvncserver0_0.9.3.dfsg.1-1ubuntu2_i386.deb)  404  Not Found [IP: 91.189.92.182 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/libv/libvncserver/x11vnc_0.9.3.dfsg.1-1ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/libv/libvncserver/x11vnc_0.9.3.dfsg.1-1ubuntu2_i386.deb)  404  Not Found [IP: 91.189.92.182 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


Is there a way that I can specify the proper location to download x11vnc in the installation command line?  I have to install it on a large number of machines with various Ubuntu versions and I'd prefer to have a "silver bullet", so to speak, that will work in all cases.  I'm not the only administrator of these machines and I'm afraid of updating global package servers due to the possibility of unforeseen consequences.  Thx.

---

### Post by Krytarik on 2012-01-08
Ubuntu 9.10 Karmic Koala reached End of Life in April last year, that's why the stored repo server URLs aren't valid anymore:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

So the "recommended" way to solve this would be to upgrade (fresh install) that particular machine to a current Ubuntu version, of course.

But if you may not or don't want to risk an upgrade, you could also replace the now invalid repo URLs in the "/etc/apt/sources.list" with those from the Old Releases server, like this:
```
deb http://old-releases.ubuntu.com/ubuntu/ karmic main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse
```Regards.

---

### Post by skyshrine on 2012-01-08
I tried adding those repos but got the same error.  Then I tried commenting out the other repos listed, but that didn't work.  Below is a copy of my sources file.  What needs to change in order to make x11vnc work?  Thanks.

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

---

### Post by Krytarik on 2012-01-08
> **skyshrine said:**
> I tried adding those repos but got the same error.  Then I tried commenting out the other repos listed, but that didn't work.  Below is a copy of my sources file.  What needs to change in order to make x11vnc work?
Apart from the (out-commented) CD-ROM entry, which you may re-use at a later point, simply remove everything else or out-comment it as well, and instead place the previously stated lines into it. After doing so, reload the package database by running:
```
sudo apt-get update
```

---


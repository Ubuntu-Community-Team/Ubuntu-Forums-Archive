---
title: "Update Manager Errors"
date: 2011-03-16
forum: Desktop Environments
---

### Post by HarvMan on 2011-03-16
Hi,

I am using Ubuntu desktop 10.04 LTS.  For some reason Update Manager is encountering difficulties trying to fetch updates.  How can I resolve this issue?  Thanks!

Here is a sample:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2011b-0ubuntu0.10.04_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2011b-0ubuntu0.10.04_all.deb)
  404  Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/clamav/libclamav6_0.96.5+dfsg-1ubuntu1.10.04.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/clamav/libclamav6_0.96.5+dfsg-1ubuntu1.10.04.1_i386.deb)
  404  Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/clamav/clamav-base_0.96.5+dfsg-1ubuntu1.10.04.1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/clamav/clamav-base_0.96.5+dfsg-1ubuntu1.10.04.1_all.deb)
  404  Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/clamav/clamav-freshclam_0.96.5+dfsg-1ubuntu1.10.04.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/clamav/clamav-freshclam_0.96.5+dfsg-1ubuntu1.10.04.1_i386.deb)
  404  Not Found [IP: 91.189.88.31 80]

etc, etc, etc.

---

### Post by HarvMan on 2011-03-16
Here is a copy of my sources.list:

user@ubuntu:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

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
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
user@ubuntu:~$

---

### Post by nilarimogard on 2011-03-16
Change your server to the main Ubuntu server, run an "sudo apt-get update" and try again - it should work.

---

### Post by HarvMan on 2011-03-17
Hi,

Can you please tell me what is the URL for the main Ubuntu server?  Thanks!

---

### Post by HarvMan on 2011-03-17
After digging around, the solution was just to go into Synaptic Package Manager (close update manager first) and hit the "Reload" button. Close Synaptic, then run the update manager again.

The update completed successfully!

---

### Post by Frogs Hair on 2011-03-17
To change servers go to update manager > settings > Ubuntu software tab.

---


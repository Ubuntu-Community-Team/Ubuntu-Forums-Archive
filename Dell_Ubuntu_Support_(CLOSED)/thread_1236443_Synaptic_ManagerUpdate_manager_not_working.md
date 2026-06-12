---
title: "Synaptic Manager/Update manager not working"
date: 2009-08-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by johnjoy on 2009-08-10
i'm in a lan, and i need to set a proxy to access the net. i have set it on my Synaptics, Networking tools, Networks, and browser. i'm able to visit all sites in my browser.

i have set the source server as ftp.iitm.ac.in (india). but when i try to update files, it says Could not resolve host [email]iitb@netmon.iitb.ac.in[/email]. 

the etc/apt/Source.list file says

deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
deb-src [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) jaunty main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) jaunty main restricted
deb-src [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) jaunty multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) jaunty-updates main restricted
deb-src [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) jaunty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) jaunty universe
deb [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) jaunty multiverse
  deb [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) jaunty-security main restricted
deb-src [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) jaunty-security restricted main multiverse universe #Added by software-properties
deb [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) jaunty-security universe
deb [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) jaunty-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main

i wanted to install strong dc++ and some video player. please help me run the synaptics.

Thank You

---

### Post by realzippy on 2009-08-10
...does "apt-get" work?
Open a terminal and type:

**sudo apt-get update**

if it does,it might be a gksudo synaptic problem as referred here:

[http://www.linuxquestions.org/questions/ubuntu-63/problems-with-apt-get-synaptic-and-proxy-454026/](http://www.linuxquestions.org/questions/ubuntu-63/problems-with-apt-get-synaptic-and-proxy-454026/)

---

### Post by bulls_eye on 2009-08-24
hi,
have you tried proxy settings in the terminal?
I had the same problem once and setting proxy through the terinal did the trick for me...

just open the terminal and type

export http_proxy=http://username:password@proxyserver.net:port/
export https_proxy=http://username:password@proxyserver.net:port/
export ftp_proxy=http://username:password@proxyserver.net:port/

hope this works for you too...

---


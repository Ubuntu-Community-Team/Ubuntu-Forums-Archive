---
title: "software sources country disappeared"
date: 2009-05-28
forum: General Help
---

### Post by AQ80 on 2009-05-28
hi all,

I installed ubuntu 9.04 and while trying to configure networking and updates (which is working now) I changed the server under the ubuntu software tab in software sources from Kuwait to united states .

now I can't get it back to kuwait not even in searching other countries.

and selecting best servers test fails (no sutable download server was found) even though I'm connected and updating without problems .

any ideas are appreciated.
thanks.

---

### Post by upbeat.linux on 2009-05-28
Can you post your sources.list file here?

---

### Post by AQ80 on 2009-05-31
sorry for the late reply I was out of the office for the weekend
this is the content of my sources.list
and I see a line with "http://kw.archive.ubuntu.com" but can't see Kuwait in the software sources





# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://kw.archive.ubuntu.com/ubuntu/](http://kw.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://kw.archive.ubuntu.com/ubuntu/](http://kw.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free

---

### Post by _Purple_ on 2009-05-31
Have you tried the main server?

---

### Post by AQ80 on 2009-06-01
yes I did try main but it still isn't connecting to Kuwait server 
I did a work around by installing a copy of ubuntu on virtual machine and copying the sources.list from there but this really can't be the only solution, that is just unreasonable.

surely there is a way to re-choose the "server for Kuwait" if you ever change it as there are a lot of other countries to choose from.

this is a copy of my new (old) sources.list just for future reference maybe someone will need it someday :



# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://kw.archive.ubuntu.com/ubuntu/](http://kw.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://kw.archive.ubuntu.com/ubuntu/](http://kw.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://kw.archive.ubuntu.com/ubuntu/](http://kw.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://kw.archive.ubuntu.com/ubuntu/](http://kw.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://kw.archive.ubuntu.com/ubuntu/](http://kw.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://kw.archive.ubuntu.com/ubuntu/](http://kw.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://kw.archive.ubuntu.com/ubuntu/](http://kw.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://kw.archive.ubuntu.com/ubuntu/](http://kw.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://kw.archive.ubuntu.com/ubuntu/](http://kw.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://kw.archive.ubuntu.com/ubuntu/](http://kw.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://kw.archive.ubuntu.com/ubuntu/](http://kw.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://kw.archive.ubuntu.com/ubuntu/](http://kw.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://kw.archive.ubuntu.com/ubuntu/](http://kw.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb-src [http://kw.archive.ubuntu.com/ubuntu/](http://kw.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free







also for future reference the way I changed it is the following:

Applications 
              Accessories
                             Terminal

then use this command in terminal:

sudo gedit /ets/apt/sources.list



p.s.  maybe there is a better way, I'm not sure

---


---
title: "automatic updates have stopped"
date: 2009-01-03
forum: General Help
---

### Post by dougleduck on 2009-01-03
For quite a while now automatic updates have failed to work (they are turned on in synaptic). I can update but only manually after reloading packages. The result of cat /etc/apt/sources.list is posted below. 

Thanks for any help.


```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ intrepid main restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ intrepid multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates restricted main multiverse universe

## Medibuntu - Ubuntu 7.04 “feisty fawn”
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs

# deb http://mirror.phy.bnl.gov/debian-root unstable main contrib
deb http://dl.google.com/linux/deb/ stable non-free
# deb http://mirror.phy.bnl.gov/debian-root/ubuntu gutsy main contrib
```

---

### Post by dougleduck on 2009-01-04
bump

---

### Post by dougleduck on 2009-01-05
bump again. if anyone needs more info please ask, not sure what I should be providing.

---

### Post by Therion on 2009-01-05
> **dougleduck said:**
> For quite a while now automatic updates have failed to work (they are turned on in synaptic). 
I'm not sure what you mean.  Automatic Updates happen only when certain updates become available...  

What is it, specifically, that makes you think Automatic Updates are NOT working on your system?

---

### Post by dougleduck on 2009-01-05
For what must be at least two months I have received no updates automatically. Only very occasionally (perhaps twice) I realised and manually updated. The frequency used to be one or more set of updates a week I'm pretty sure.

The updatedb program does still check for updates (I notice a change in system performance when it does) but never finds any.

---

### Post by n00ne on 2009-01-16
I have the same problem.
don't know if the system tries to update and fail but I don't get any automatic uodates.
updating manually every few days usually find new updates
and if I don't remember to run it after about two weeks I get a yellow alert icon in the task bar notifing me the system is out of date and
that I should check manually for updates.
every thing is configured to run automatic, used to work on 8.04 before I upgraded

---

### Post by PriceChild on 2009-01-16
Go to system > administration > software sources

Choose the Updates tab, and check the "check for updates" checkbox is checked (wow that was a lot of checks) and what button the choice the policy on whether to install or notify is set to.

---

### Post by zika on 2009-01-16
beside that series of checks in Software_sources just one more check: System->Preferences->Sessions->Update_notifier

---

### Post by n00ne on 2009-01-21
all of this was already configured updates should be checked daily
and update-notifier is up and runing

---

### Post by OboeNerd on 2009-01-21
I have this problem in Canada, try switching to the main server instead of your local one.

System->Administration->Software Sources

Switch the Download from: to the Main Server.

I'm not sure if it works in your area, but here in Canada this fix works.

---

### Post by n00ne on 2009-01-22
ok. I've doen that. lets hope it'll work
let you know in a few days...

---

### Post by n00ne on 2009-01-27
ok this didn't work.

any other ideas ?

---


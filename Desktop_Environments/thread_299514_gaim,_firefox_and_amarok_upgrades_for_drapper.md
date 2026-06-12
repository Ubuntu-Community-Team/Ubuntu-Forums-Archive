---
title: "gaim, firefox and amarok upgrades for drapper"
date: 2006-11-14
forum: Desktop Environments
---

### Post by BooVeMan on 2006-11-14
Hi there!

so this might be bulling but gaim turned 2.0.0beta5, firefox officially released 2.0, amarok advanced to 1.4.4 - anyone has pointers how to upgrade the lot in drapper? I know LTS implies stability - but after a few weeks testing may be through and upgrades should at least be available - the may be tagged recommended or whatever - but at least available - or is this to demanding? :rolleyes: 

Regards,
Burkhard

---

### Post by marianom on 2006-11-14
As far as I know, only security fixes for those programs will going to be available (as it happened with firefox where we got a security upgrade) from the official repos. New versions are not included.
So two options:
1- find a .deb package or compile the programs from source
2- upgrade to edgy.

In my case, since I'll stick with dapper for the next months, I'll use option 1.

---

### Post by TheWizzard on 2006-11-14
> **BooVeMan said:**
> Hi there!

so this might be bulling but gaim turned 2.0.0beta5, firefox officially released 2.0, amarok advanced to 1.4.4 - anyone has pointers how to upgrade the lot in drapper? I know LTS implies stability - but after a few weeks testing may be through and upgrades should at least be available - the may be tagged recommended or whatever - but at least available - or is this to demanding? :rolleyes: 

Regards,
Burkhard

a first step is to enable the backports. amarok 1.4.3 is available in the backports. 
firefox is a different story. the easiest is to use aysiu's script [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by BooVeMan on 2006-11-14
hmm already do have amarok 1.4.3 - 1.4.4 seems to have flashy new features, firefox will I try - so what about gaim - I'm trying to have amarok sending its currently played song to gaim with the AmarokGaim-script but it fails.

---

### Post by TheWizzard on 2006-11-15
> **BooVeMan said:**
> hmm already do have amarok 1.4.3 - 1.4.4 seems to have flashy new features, firefox will I try - so what about gaim - I'm trying to have amarok sending its currently played song to gaim with the AmarokGaim-script but it fails.

i don't know. i don't use gaim. 

not every new version of each program makes it to the backports. please note that for each distribution there's a balance between stability and having the newest of the newest. ubuntu focusses much on stability. if you want cutting edge software you may want to try a different distro. but bleeding edge distro's are less stable.

---


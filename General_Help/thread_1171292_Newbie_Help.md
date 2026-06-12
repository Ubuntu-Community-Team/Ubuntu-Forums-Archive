---
title: "Newbie Help"
date: 2009-05-27
forum: General Help
---

### Post by will547_us on 2009-05-27
Greetings,
 
I bought a laptop with 8.04 installed and after following all the tips for beginners thought I might try an upgrade. I was unsure how to do a back up so I tried to load Remastersys and I thought I had done so sucessfully. NOT!!
 
I received this error:
 
E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
 
I am unsure how to recomment the sources list or enter the repository dialog to correct my error. Can someone assist me with this?
 
TIA, Will

---

### Post by albinootje on 2009-05-27
> **will547_us said:**
> 
E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)

Can you post your /etc/apt/sources.list here ?

---

### Post by will547_us on 2009-05-27
I have the Synaptic manager working again after unclicking the Remastersys repository. I'm still unsure how to back up per the upgrade instructions.
 
This my list, I think.
 
## deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to# newer versions of the distribution.
 
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted 
## Major bug fix updates produced after the final release of the
## distribution.deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe         16
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
 
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse   33
 
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb [http://ppa.launchpad.net/dell-team/ubuntu](http://ppa.launchpad.net/dell-team/ubuntu) hardy main
# deb-src [http://ppa.launchpad.net/dell-team/ubuntu](http://ppa.launchpad.net/dell-team/ubuntu) hardy main     41
 
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe
 
# Remastersys
deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys
 
The numbers to the side are my line count and I don't see a line 56 ???
 
 Cheers, Will

---

### Post by will547_us on 2009-05-27
When I enter /etc/apt/sources.list in Terminal I get :
 
bash: /etc/apt/sources.list: permission denied

---

### Post by feelshift on 2009-05-27
> **will547_us said:**
> When I enter /etc/apt/sources.list in Terminal I get :
 
bash: /etc/apt/sources.list: permission denied

You should enter
```
sudo gedit /etc/apt/sources.list
```
And then your password ;)

---

### Post by albinootje on 2009-05-27
> **will547_us said:**
> 
# Remastersys
deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys
 
The numbers to the side are my line count and I don't see a line 56 ???


Your line 56 is about remastersys.
And according to this [http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html) the line should like this instead :
```

deb http://www.geekconnection.org/remastersys/repository ubuntu/

```

---

### Post by will547_us on 2009-05-27
Thank you albinootje!!

---


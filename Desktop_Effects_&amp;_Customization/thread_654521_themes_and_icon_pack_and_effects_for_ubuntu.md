---
title: "themes and icon pack and effects for ubuntu"
date: 2007-12-31
forum: Desktop Effects &amp; Customization
---

### Post by karq on 2007-12-31
So where can I get these things for ubuntu 7.10?

---

### Post by Forlong on 2007-12-31
Themes and icons mainly on [http://gnome-look.org](http://gnome-look.org)

Desktop effects are pre-installed in Ubuntu Gutsy. Just go to *System &#8594; Preferences &#8594; Appearance &#8594; Visual Effects*
If it's not working, post the output of ```
compiz
``` in a terminal.

---

### Post by karq on 2007-12-31
so can someone tell me how can i install compiz on ubuntu 7.10? I think i just remove those visual effects what where preinstalled :S made a big mistake. and how can i install emerald ?

---

### Post by Forlong on 2007-12-31
```
sudo apt-get install compiz emerald compizconfig-settings-manager
```

---

### Post by karq on 2007-12-31
see ei aidanud 
 lööb sellise:


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz: Depends: compiz-decorator
  emerald: Depends: libemeraldengine0 but it is not going to be installed
           Depends: libwnck18 (>= 2.15.90) but it is not installable
E: Broken packages

---

### Post by Forlong on 2007-12-31
Hm... what does your sources.list look like:
```
cat /etc/apt/sources.list
``` and use the forum's CODE tag please (# button)

---

### Post by karq on 2007-12-31
[html]kaarel@kaarel:/$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main aiglx
kaarel@kaarel:/$ 

[/html]

it looks like this.

---

### Post by Forlong on 2007-12-31
Ubuntu's codename for 7.10 is Gutsy (Gibbon) but you have sources for Feisty (7.04) and even Dapper (6.06) in there.

Open the file being root:
```
sudo gedit /etc/apt/sources.list
```
Then delete those lines:
```
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
deb http://ppa.dogfood.launchpad.net/amaranth/ubuntu feisty main
deb http://www.beerorkid.com/compiz dapper main aiglx
deb http://media.blutkind.org/xgl/ dapper main aiglx
deb http://ubuntu.compiz.net/ dapper main aiglx
```

Afterwards go to *System &#8594; Administration &#8594; Software Sources* and check (at least) main, universe and restricted.
Then update your sources:
```
sudo apt-get update && sudo apt-get upgrade
```
And try to install Compiz again:
```
sudo apt-get install compiz emerald compizconfig-settings-manager
```

---

### Post by karq on 2007-12-31
thx alot it works now, but how an i make that cube?

---

### Post by Forlong on 2007-12-31
See [here](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion) under "Getting the cube".

---

### Post by shabuntu on 2008-01-01
I have 7.10 on my new laptop R61i. Visual effects doesn't work. Wondering if someone can tell me how to get it work.

$compiz
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 

Thanks

---

### Post by Forlong on 2008-01-06
Try running Compiz like this: ```
SKIP_CHECKS=yes compiz
```

---


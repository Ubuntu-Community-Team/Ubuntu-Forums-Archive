---
title: "Apt-get hanging"
date: 2006-06-17
forum: Desktop Environments
---

### Post by Alpha_Cluster on 2006-06-17
I started iwth a fresh install and attempted to get all my basic stuff through EasyUbuntu.  But while i ran that apt hung at the flashplugin.  I had to kill apt in order to stop it.  now whenever i try and apt something i get an error telling me"
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."
I keep trying to run that command but everytime the flashplugin hangs. Is there someway to stop this.

---

### Post by sgarrand on 2006-06-19
I'm having the same problem. No one in IRC is responding and I'm getting pretty frustrated. :)

Scott

---

### Post by FredB on 2006-06-19
You don't really need Easy Ubuntu to grab flash and Java for instance. If you have a nvidia card, either.

So, try removing flash plugin for now using sudo apt-get remove flash-plugin - or using synaptic.

Can you also post your /etc/apt/sources.list ?

---

### Post by sgarrand on 2006-06-19
I can install Flash separately but I can't get apt-get (and Synaptic) to work now that it's stuck.

Scott

Edit: My sources.list:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
# The above lines were generated automatically by EasyUbuntu 3.0 Beta Release
# The rest of your sources.list follows

#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by Alpha_Cluster on 2006-06-19
I solved my problem by reinstalling but i was wondering if there is a method to fix it without having too.  And i dont NEED to use EasyUbuntu its just well easier.

---


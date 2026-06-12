---
title: "Upgrading problems"
date: 2011-11-04
forum: Desktop Environments
---

### Post by Chame_Wizard on 2011-11-04
How can I upgrade from KSC 4.5.3 to 4.7.3 on Kubuntu 10.04.2 LTS x64 with kernel 3.0.8-030008-generic?

I tried with 4.7.0(individual .deb files via launchpad),but it's refusing.

I already added the "backports" and "Kubuntu updates" PPA long ago,but for some reason the various PPA aren't really working/upgrading.Something must be wrong with the sources.list.


:confused:

---

### Post by schnelle on 2011-11-05
KDE 4.7 is only packaged for Natty (you can install it from kubuntu-ppa) and for Oneiric.

If you want to use KDE 4.7.2 and newer bugfix releases (4.7.3,4.7.4) you have to use Oneiric.

---

### Post by Chame_Wizard on 2011-11-05
> **schnelle said:**
> KDE 4.7 is only packaged for Natty (you can install it from kubuntu-ppa) and for Oneiric.

If you want to use KDE 4.7.2 and newer bugfix releases (4.7.3,4.7.4) you have to use Oneiric.

Are you saying I have to do a distro upgrade???

```
luzomes_chrishi@JMWF-CPT:~$ sudo apt-get install update-manager-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
update-manager-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
luzomes_chrishi@JMWF-CPT:~$ sudo do-release-upgrade
Checking for a new ubuntu release
No new release found
luzomes_chrishi@JMWF-CPT:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```:confused:

---

### Post by schnelle on 2011-11-16
> **Chame_Wizard said:**
> Are you saying I have to do a distro upgrade???

```
luzomes_chrishi@JMWF-CPT:~$ sudo apt-get install update-manager-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
update-manager-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
luzomes_chrishi@JMWF-CPT:~$ sudo do-release-upgrade
Checking for a new ubuntu release
No new release found
luzomes_chrishi@JMWF-CPT:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```:confused:

I am saying that if you want to use KDE 4.7 then you have to use Kubuntu 11.10. And better make clean (new) install of Kubuntu 11.10. Upgrade from 10.04 to 11.10 will probably end up in broken system. Command for upgrading is ```
sudo do-release-uprade
``` But I [COLOR="Red"]do not[/COLOR] recommend it. Best way is to do a clean install.

---

### Post by mister_playboy on 2011-11-16
> **Chame_Wizard said:**
> Are you saying I have to do a distro upgrade???

Trying to run the latest and greatest while sticking to an older release is contradictory... you have to choose one or the other. ;)

---


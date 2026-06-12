---
title: "Minor Breezy/OO.o issue"
date: 2005-10-14
forum: Desktop Environments
---

### Post by stray on 2005-10-14
I've just completed my upgrade to Breezy. Spectacular! However, I tried to install language-pack-en and the other language packs I was advised to by the [upgrade notes](https://wiki.ubuntu.com/BreezyUpgradeNotes) and I keep getting this error when I try to apply updates in Synaptic:
> E: /var/cache/apt/archives/openoffice.org2-help-en-us_1.9.129-0.1ubuntu5_all.deb: trying to overwrite `/usr/lib/openoffice2/help/en/scalc.idx/DOCS.TAB', which is also in package openoffice.org2-calc
Anyone know what this means? According to Synaptic, *language-support-en* is a broken package. Do I even need it? Can anyone help me out here?

---

### Post by DJ_Max on 2005-10-14
The same exact thing happen during my upgrade, and it bonked out on me.

This is what I did, not sure if there is an easier way.
I had to remove all the openoffice.org2-* packages (openoffice.org2-calc, openoffice.org2-draw, etc..)

```
sudo dpkg -r openoffice.org2-calc #For each package
``` 
Then
```
sudo apt-get -f install
```
If it fails again. it will tell you which package is in the way. Then remove it.

Run it again, it should continue to install a bunch of packages

Also may want to
```
sudo apt-get dist-upgrade
```

---


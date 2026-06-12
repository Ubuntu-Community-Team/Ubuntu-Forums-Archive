---
title: "Compiz Problems"
date: 2009-04-30
forum: General Help
---

### Post by venomizer on 2009-04-30
Hi all, I'm running the UNR on my MSI Wind and I'm having some problems with Compiz.

I've been trying to install it, and i'm able to mark all packages to install through SPM apart from compizconfig-settings-manager which comes up with this error when I mark it for installation:

> The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.

compizconfig-settings-manager:

Depends: python-compizconfig (>=0.8.2) but it is not installable

I've done a search in SPM for python-compizconfig, but it returns nothing.

I'm a bit of a Linux noob so I might be missing something simple.  I think most of the compiz effects have been enabled (are the wobbly windows, automatic snapping to full screen etc. compiz effects? Or are they standard with Ubuntu?), but I can't access the manager to alter their settings (which is presumably what this package is for...)


Thanks

---

### Post by delcypher on 2009-04-30
I'm not sure how different UbuntuNetbookRemix is from Ubuntu Desktop edition but I can see python-compizconfig. It is in the universe repository.

It is likely you don't have the repository enabled or that your cache is out of date.

1. Make sure you have the repository enabled. Go into "Administration > Software sources" and make sure that universe is enabled.

Alternatively you can add it manually by editing /etc/apt/sources.list and adding the line
```
deb http://gb.archive.ubuntu.com/ubuntu intrepid-security universe

```

or 

```
deb http://gb.archive.ubuntu.com/ubuntu jaunty-security universe

```

depending on which version of UNR you are using. You can find out using```
cat /etc/lsb-release
``` in the terminal. Codename is the bit you are looking for.

2. Refresh your package cache. To do this type the following into the terminal```
sudo apt-get update
```

Now try installing the python-compizconfig
```
sudo apt-get install python-compizconfig

```

now try to install compiz settings manager
```
sudo apt-get install simple-ccsm
```

---


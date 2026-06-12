---
title: "I can't update"
date: 2006-01-03
forum: Desktop Environments
---

### Post by Naxuz on 2006-01-03
I just switched and installed Ubuntu today. Otherwise it is working nicely... but I can't update my system or download anything through Synaptic. When I try to update through Software Updates, it shows me the packages that have updates available, and when I click "Install", it downloads the updates and when it gets to the "The updates are being applied...", it throws an error message at me that says the following:

```
E: /var/cache/apt/archives/perl-modules_5.8.7-5ubuntu1.2_all.deb: files list file for package `xserver-xorg-input-magellan' contains empty filename

```

Then pops the "Upgrade Finished"-window, which tells me to look at the terminal buffer. It says the following:

```
Extracting templates from packages: 100%
Preconfiguring packages ...
( Reading database ... dpkg: error processing  /var/cache/apt/archives/perl-modules_5.8.7-5ubuntu1.2_all.deb (--unpack):
files list file for package `xserver-xorg-input-magellan' contains empty filename
```

What to do? My friends say they've had no such problems while updating.

EDIT: Oh yeah, the downloading through Synaptic gave me a similar response.

---

### Post by Naxuz on 2006-01-03
I can't even begin to fathom what was wrong, but a reinstall solved it.

---


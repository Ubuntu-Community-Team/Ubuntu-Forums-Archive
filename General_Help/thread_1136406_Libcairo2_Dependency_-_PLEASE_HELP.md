---
title: "Libcairo2 Dependency - PLEASE HELP"
date: 2009-04-25
forum: General Help
---

### Post by Rezaki on 2009-04-25
I just upgraded to Hardy from Gutsy. I have installed libpango 1..0.0-common and now am attempting to install libpango1..0.0 (even though it says it is already installed) so that I can satisfy a dependency and install flash in firefox 3. However, now it says I have to satisfy a dependency on libcairo2. Libcairo 2 is also already installed, I reinstalled it and also installed every package related to libcairo2 and it still will not let me install libpango or flash. I see lots of posts about the libpango dependency but not the libcairo2. Anyone dealt with this?  Thank you!-Wally

---

### Post by hansdown on 2009-04-25
Hi Rezaki.

Go to system> administration> synaptic package manager.

Search for flashplugin-nonfree.

---

### Post by Rezaki on 2009-04-25
Ok so I tried uninstalling flashplugin-nonfree and reinstalling libpango1.0.0 and restarting ubuntu and firefox and it still won't let me install the flash .deb file because of the libpango dependency. I have attempted to use the links people give in fixes for this to download libpango from the web and it states a libcairo2 dependency issue when I try to install libpango1.0.0 even though libpango1.0.0 AND libcairo2 are already installed! When I reinstall libcairo2 and libpango1.0.0 on synaptic everything works fine. If anybody has any ideas it would be great cause this is really frustrating! Thank you!

---

### Post by mc4man on 2009-04-25
First try going to System -> Admin. -> Software Sources -> Updates and make sure first 2 boxes are checked. (particulary hardy-updates
If not enabled, then enable, click close and reload (or go sudo apt-get update
Then try again

If no go there try installing one of these packages from the terminal and post output ( libcairo2 or libpango1.0-0

Or go into synaptic and post the version #'s of libcairo2 : libpango1.0-0  : libpango1.0-common

---

### Post by hansdown on 2009-04-25
As far as flash in ff 3, here is something that should help.

[http://chi3x10.wordpress.com/2009/02/01/install-flash-player-for-firefox-in-ubuntu-804/](http://chi3x10.wordpress.com/2009/02/01/install-flash-player-for-firefox-in-ubuntu-804/)

You should also re-install flash plug-in non-free in synaptic, as it is needed for some things.

Do you have ubuntu-restricted-extras installed?

---

### Post by Rezaki on 2009-04-25
Ok the software sources boxes are now checked. It now let me reinstall libpango1.0-0 from the packages site without saying I needed libcairo2. HOWEVER, it still says I need libpango1.0.0 when I try to install flash. These are the versions I have installed according to synaptic: libpango1.0-0: 1.20.1-1 (latest version) and libpango1.0-common: 1.22.2-0ubuntu1 (latest version). Any ideas? Thank you all for your help.

---

### Post by mc4man on 2009-04-25
For some reason your still at *hardy* versions verus *hardy-updates*, I'd try to get updated to current hardy update versions first before worring about flash

Maybe try, if you've enabled hardy-updates
 ```
sudo apt-get update && sudo apt-get upgrade
```

For instance here's the hardy-update ver. of libpango1.0-common
[http://packages.ubuntu.com/hardy-updates/libpango1.0-common](http://packages.ubuntu.com/hardy-updates/libpango1.0-common)

You could try a direct install from there and see what the gdebi error message is


Maybe post your sources.list

```
cat /etc/apt/sources.list
```


On hardy I use the adobe flash player, works great (I prefer over the repo version
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

---


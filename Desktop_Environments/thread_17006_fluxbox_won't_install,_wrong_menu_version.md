---
title: "fluxbox won't install, wrong menu version"
date: 2005-02-25
forum: Desktop Environments
---

### Post by negatron on 2005-02-25
I downloaded the fluxbox_0.9.11-1_i386.deb from [http://logicvortex.net/debian/fluxbox/](http://logicvortex.net/debian/fluxbox/) and tried to install it with dpkg. And I get an error like this:
```

negatron@kiipeilyteline:~ $ sudo dpkg -i fluxbox_0.9.11-1_i386.deb
(Reading database ... 112788 files and directories currently installed.)
Preparing to replace fluxbox 0.9.11-1 (using fluxbox_0.9.11-1_i386.deb) ...
Unpacking replacement fluxbox ...
dpkg: dependency problems prevent configuration of fluxbox:
 fluxbox depends on menu (>= 2.1.19); however:
  Version of menu on system is 2.1.14.
dpkg: error processing fluxbox (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fluxbox

```
How can I update that menu thingie? I've tried "apt-get update", "apt-get upgrade" and "apt-get dist-upgrade". And still it won't work. :|

---

### Post by ThePrawn on 2005-03-02
Any luck?

---

### Post by SurreaL on 2005-03-03
negatron, I've been able to fairly easily compile fluxbox from source.. I would suggest you try the same thing :) (Easy as downloading the source, and running "./configure" -> "make" -> "make install") I'm sure you'd probably need an update menu package though.. which I don't remember installing, but I must have since it's showing up in synaptic.

It looks like I got it from the universe repository, so you might have to enable that to get to install the package. You can do so by doing a
sudo nano /etc/apt/sources.list

read through the file and look for the repositories that say universe and have a # indicating they are commented out.. after removing those comments you should be able to have access to v 2.1.20 of Menu :)

I think you're making a good move with fluxbox btw, I've found I enjoy it the most out of the handful I've tried (sawfish, xfce4, ice, and now this) For whatever reason the default menu didn't install properly for me however.. so be prepared to run fluxbox-generate_menu to get that working as well.

I've gotten somewhat familiar with it over the past two days I've been using it, so if you have any more questions go ahead and post 'em :)

---


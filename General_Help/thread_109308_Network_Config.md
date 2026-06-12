---
title: "Network Config"
date: 2005-12-28
forum: General Help
---

### Post by d11wtq on 2005-12-28
Hi,

In general terms to using Linux I'm still pretty new (1 year).  I used SuSE for a couple of months... then I made a HUGE switch from that GUI based distro and moved to Gentoo.  I love Gentoo... I like the fact I can see what's going on rather than having a GUI disguise it all.  Using Gentoo has made me a bit of a command-line junkie.

Just yesterday I installed Breezy Badger on another partition since I believe it may be more suited as a desktop system than Gentoo which makes you compile everything (yawn :P).

I've managed to get my wireless running using ndiswrapper and iwconfig/ifconfig but I can't seem to find the config files to edit to make my configurations permanent.  Where would I find these files?  In SuSE they are /etc/sysconfig/network  and in Gentoo they are /etc/conf.d/net but neither of these paths exist in Ubuntu.

Many thanks,

d11wtq

---

### Post by Lambert on 2005-12-28
etc/network/interfaces

there's a man page for this file

man interfaces

there's also a file in /usr/share/doc/ifupdown/examples called network-interfaces.gz


The basics of how networking in debian based distro is done can be found here.

[http://www.debian.org/doc/manuals/reference/ch-gateway.en.html](http://www.debian.org/doc/manuals/reference/ch-gateway.en.html)

---

### Post by d11wtq on 2005-12-28
[QUOTE=Lambert]etc/network/interfaces

there's a man page for this file

man interfaces

there's also a file in /usr/share/doc/ifupdown/examples called network-interfaces.gz


The basics of how networking in debian based distro is done can be found here.

[http://www.debian.org/doc/manuals/reference/ch-gateway.en.html](http://www.debian.org/doc/manuals/reference/ch-gateway.en.html)[/QUOTE]

Brilliant, thank you :D

---


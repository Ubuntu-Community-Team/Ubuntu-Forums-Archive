---
title: "Gtk-Gnutella, how to use???"
date: 2005-12-19
forum: General Help
---

### Post by Prudentissimus on 2005-12-19
Hello!


       I have the 0.95.4 stable edition; It appears that nothing turns out when I search... - no results...

       And it says that I am running in leaf mode and firewalled? ... Is that why I cannot get any results??? How do I remove firewall? (I dun think I have any firewall...)

---

### Post by Gastric ReFlux on 2005-12-20
[QUOTE=Prudentissimus]Hello!


       I have the 0.95.4 stable edition; It appears that nothing turns out when I search... - no results...

       And it says that I am running in leaf mode and firewalled? ... Is that why I cannot get any results??? How do I remove firewall? (I dun think I have any firewall...)[/QUOTE]

I installed Ubuntu last week, and over the weekend, used Synaptic to install it.  I got the same message as you.

I solved it by downloading the latest Debian package from the sourceforge site.

[http://gtk-gnutella.sourceforge.net/en/?page=news](http://gtk-gnutella.sourceforge.net/en/?page=news)

I downloaded it via Firefox to my desktop, then opened up a terminal, cd'd to my Desktop, and entered in the command line:

dpkg -i Gtk-gnutella096debinapackage.deb

Of course don't just copy and paste my example there, use the actual name of the deb package file.

0.96 will work for you, most likely.

---

### Post by Gastric ReFlux on 2005-12-20
See, from the sourceforge site, there's this bit of info:

> Version 0.96b is a beta version of forthcoming 0.96. It is now mandatory to use this beta version as the 0.95.x series is about to expire on November 26th.

It looks like the network won't recognize requests from versions < 0.96, and Ubuntu's package of 0.95 available through Synaptic won't work at this point.

---


---
title: "gtk-gnutella 0.95.4 stable"
date: 2005-12-21
forum: Desktop Environments
---

### Post by lesliem on 2005-12-21
Hi all,
Have recently downloaded gnutella, install seemed alright, but program when opened does not run/connect with network. I suspect something to do with firewall/port not opening.
Have tried gnutella/ubuntu settings but no response.
Anybody had similar problems?, would appreciate help. I've used gnutella on other linux distros this is first time "no play".

---

### Post by adie273 on 2005-12-21
I've installed gtk-gnutella recently using synaptic, and it won't even run for me. 

Not sure why. :???: 

Adie

---

### Post by Gastric ReFlux on 2005-12-21
[QUOTE=adie273]I've installed gtk-gnutella recently using synaptic, and it won't even run for me. 

Not sure why. :???: 

Adie[/QUOTE]

The problem is this as stated on the GTK-gnutella.sourceforge.com site.

> 22 November 2005, Version 0.96b Released

Version 0.96b is a beta version of forthcoming 0.96. It is now mandatory to use this beta version as the 0.95.x series is about to expire on November 26th. 

I believe that means that any version < 0.96 will not connect to the gnutella network.

You'll need to go to their download page, and use that to download the debian package, and with that, you can use a terminal and the command line to install 0.96

```
dpkg -i GTK2_gtk-gnutella_0.96.0-0_i386.deb
```

did the trick for me after I navigated to the folder I had downloaded the package to.

---

### Post by adie273 on 2005-12-22
Nice one, Cheers Gastric ReFlux

Adie

---


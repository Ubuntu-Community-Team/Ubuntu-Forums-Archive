---
title: "Firefox for Debian"
date: 2008-08-13
forum: Debian
---

### Post by molom on 2008-08-13
I know Iceweasel is there, but it isn't updated as quick as Firefox. Is it possible to install Firefox 3.0 on Debian?

---

### Post by ibutho on 2008-08-13
Its possible. I use the official Firefox 3.x builds from the Mozilla site on Debian Testing. Simply extract the tarball to a directory of your choice e.g. /opt, create any symlinks you wish to plugins such as flash. Also change the default browser in GNOME, KDE, XFCE etc to your version of Firefox.

---

### Post by eeezzzeee on 2008-08-15
I tried following a couple of tutorials off the net for this, but everytime I tried to launch firefox it would bring up iceweasel. I even tried uninstalling iceweasel via synaptic, but it still brought up iceweasel. Any thoughts as to what I could remove or do?

---

### Post by L815 on 2008-08-16
Try removing Firefox, then running:
```
sudo apt-get autoremove
```

Then try reinstalling Firefox

---

### Post by kerry_s on 2008-08-16
> **molom said:**
> I know Iceweasel is there, but it isn't updated as quick as Firefox. Is it possible to install Firefox 3.0 on Debian?

if your using etch->
[http://www.linuxscrew.com/2008/06/21/install-firefox-3-in-debian-etch/](http://www.linuxscrew.com/2008/06/21/install-firefox-3-in-debian-etch/)

---

### Post by molom on 2008-08-16
Thanks for the info everyone! So is there any other repo that includes recent updates of Firefox for Debian Testing?

---

### Post by kerry_s on 2008-08-16
> **molom said:**
> Thanks for the info everyone! So is there any other repo that includes recent updates of Firefox for Debian Testing?

try this: [http://ftp.us.debian.org/debian/pool/main/i/iceweasel/iceweasel_3.0.1-1_i386.deb](http://ftp.us.debian.org/debian/pool/main/i/iceweasel/iceweasel_3.0.1-1_i386.deb)

---

### Post by molom on 2008-08-16
> **kerry_s said:**
> try this: [http://ftp.us.debian.org/debian/pool/main/i/iceweasel/iceweasel_3.0.1-1_i386.deb](http://ftp.us.debian.org/debian/pool/main/i/iceweasel/iceweasel_3.0.1-1_i386.deb)

When I say Firefox, I don't mean Iceweasel ;)
But its iceweasel 3, so I guess I can deal with it :D

---

### Post by Oldsoldier2003 on 2008-08-16
Debian has issues with the licensing of FF, so if you want Firefox (instead of iceweasel), your best bet is to compile it. There are probably .debs out there that are 3rd party but its really not that hard to compile.

---

### Post by molom on 2008-08-16
> **Oldsoldier2003 said:**
> Debian has issues with the licensing of FF, so if you want Firefox (instead of iceweasel), your best bet is to compile it. There are probably .debs out there that are 3rd party but its really not that hard to compile.

Thanks, just wandering if I ever make a debian based distro, what is the best way to keep the communities Firefox updated without them compiling a new Firefox whenever there is a new release.

Cheers,
molom

---


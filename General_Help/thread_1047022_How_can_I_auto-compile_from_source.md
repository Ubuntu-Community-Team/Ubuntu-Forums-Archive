---
title: "How can I auto-compile from source?"
date: 2009-01-22
forum: General Help
---

### Post by grndslm on 2009-01-22
Trying to figure out if there's a way in Ubuntu to auto-compile from source, similar to FreeBSD.  I know I can download sources with Ubuntu, but I'm not even really sure what it does with them after that.  I tried downloading bsdgames to test it out, and I can't even find the source now.  It's not in /usr/src/ that's for sure.

I guess dependencies just aren't built into the sources with Debian-based distros.  What a bummer.  Perhaps something could be written to use the packages dependencies and then compile in that order, one by one??  Could it work?

I'd love to install a minimal Ubuntu install and then let "apt-get source gnome" (does aptitude even handle sources?) handle all the work from compiling xorg to all its dependencies, gnome and all its dependencies, its applets, etc.  Is it possible?

If not, is there another distro you could recommend that does both packages *and* auto-compiling of a source and that source's dependencies??  Please don't recommend Gentoo as it doesn't have pre-compiled packages available if I'm in a jam.

---

### Post by Ahadiel on 2009-01-22
Archlinux has both binary packages, and PKGBUILDS for easy compiling/dependancy grabbing ([http://aur.archlinux.org/](http://aur.archlinux.org/)).

---

### Post by bigbrovar on 2009-01-22
have u tried sudo apt-get build-dep packagename .. what this does is to download the dependencies needed for building a package from source. so in your example ```
sudo apt-get source gnome
``` should be followed by ```
sudo apt-get build-dep gnome
``` .. the first command downloads the source package for gnome while the second installs all the dependencies needed for compiling the gnome from source.

---

### Post by jerome1232 on 2009-01-22
Just thought I'd mention you don't need to run apt-get as root when grabbing source code, it actually gets downloaded to your users home directory

```
apt-get source packagename
```

---

### Post by grndslm on 2009-01-22
Thanks for the apt-get tips, guys.  If I wanted to compile all packages on a Debian-based system... it looks like I'd be best off just downloading the sources and doing everything by hand.  The lame part about that is that I have to constantly watch the machine, otherwise it'll just be idling since it wouldn't know what to do next.

The Arch ABS system is interesting, but I still dunno if it's as automatic as FreeBSD's ports.  Guess I'll have to look into it.

---


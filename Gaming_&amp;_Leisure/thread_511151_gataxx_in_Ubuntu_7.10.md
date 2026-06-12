---
title: "gataxx in Ubuntu 7.10"
date: 2007-07-27
forum: Gaming &amp; Leisure
---

### Post by Some_Person on 2007-07-27
Just install the attached deb file! :)

---

### Post by ebichu on 2007-07-27
what is it?

---

### Post by Some_Person on 2007-08-06
gataxx is the Ataxx game that was removed from Ubuntu (because it was removed from gnome-games) in an earlier version.

---

### Post by hikaricore on 2007-08-06
This tThis thread seems well intentioned, but in the future please post more details about what you're posting and where the packages came from so that it doesn't seem quite as suspicious.  ^_^

**_Ubuntu users, please only install packages from trusted sources.  Not to discourage use of this package, just a reminder._**

---

### Post by Some_Person on 2007-08-13
Package source:
[ftp://fr2.rpmfind.net/linux/conectiva/snapshot/i386/RPMS.gnome/gnome-games-xxgata-2.8.0-68685cl.i386.rpm](ftp://fr2.rpmfind.net/linux/conectiva/snapshot/i386/RPMS.gnome/gnome-games-xxgata-2.8.0-68685cl.i386.rpm)
I converted it to .deb with Alien, and replaced the actual binary with the one from Edgy to fix a display problem. This is not a virus or any sort of crapware.

---

### Post by metoor30 on 2007-11-09
Works great, thanks!  I was bumbed when I upgraded and my favorite game was gone.

---

### Post by Vadi on 2007-11-09
Yeah, the package installer can't open it in 7.10, says archive corrupted.

I don't know how to use dpkg either. Could you post a .deb for 7.10?

---

### Post by Some_Person on 2007-11-10
Use sudo dpkg --install /path/to/package.deb. For some reason GDebi doesn't like this one, on 7.04 or 7.10.

**EDIT:** I just rebuilt the package, so now it works fine with GDebi.

---


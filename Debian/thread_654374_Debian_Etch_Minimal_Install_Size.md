---
title: "Debian Etch Minimal Install Size"
date: 2007-12-31
forum: Debian
---

### Post by FakeOutdoorsman on 2007-12-31
About how much space would a minimal or command-line only install of Debian 4.0 (Etch) take up?  I ended up with 750 MB, but that seems way too large.  I installed with debian-40r1-i386-businesscard.iso.   Ubuntu Gutsy command-line install for me used about 476 MB and CentOS 5.1 took up a gorillaesque 653 MB.

---

### Post by mojoman on 2008-01-04
I'm not sure how much a CLI install would be but yes, that is too much. I've had a laptop with smaller system than that, and it had X-server installed with fluxbox (though I made sure it only installed the trident and vesa driver and I unchecked all alternatives, doing only the bare minimum install). I used the regular install DVD but the netinstall CD might be a good alternative too. Anyway, my guess is that you should be able to get this down to at least 350 MB.

/mojoman

---

### Post by maybeway36 on 2008-01-04
Uncheck "Desktop environment" and "standard system", then install anything you want with APT.

---

### Post by benuski on 2008-01-04
I just installed a server from the normal Debian install cd.  I unchecked everything at the install additional software screen, and I've install Apache2, OpenSSH, and thats about it, and my install is at about 350mb.

---


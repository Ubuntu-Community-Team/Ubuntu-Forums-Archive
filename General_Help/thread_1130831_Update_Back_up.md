---
title: "Update Back up?"
date: 2009-04-20
forum: General Help
---

### Post by ravi_buz on 2009-04-20
Hai i installed ubunt 8.04.1 and updates to 8.04.2 now can i keep a back up of all the updates so that i could use it if i need to reinstall ubuntu , you see i have a slow net connection and it will take days to install all updates again

---

### Post by kpkeerthi on 2009-04-20
The downloaded updates (.deb files) can be found in /var/cache/apt/archives folder. If you have ever run 'sudo apt-get clean', the folder would be empty as the command would wipe them clean.

---

### Post by boof1988 on 2009-04-20
One option you can check out is [*aptoncd*](http://aptoncd.sourceforge.net/).  It can make an iso that contains all of the packages/updates that you have installed after the initial installation.  These packages can then be installed again (without downloading them again) if you re-install your OS.

If you want an option that lets you make an installation disk of your existing system, then [*remastersys*](http://en.wikipedia.org/wiki/Remastersys) may be an option to check out.  it will allow you to install (on almost any computer) your existing ubuntu OS.

---


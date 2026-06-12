---
title: "Squid / Tiny Proxy Wants to Remove desktop-ubuntu (?!)"
date: 2008-04-08
forum: Desktop Environments
---

### Post by dochood on 2008-04-08
Hello, all....

I tried to install squid, and then tinyproxy, on my desktop system.  apt-get told me it was going to remove a whole bunch of packages, including evolution and ubuntu-desktop!  I'm on Hardy Heron Beta.  Previous editions of Ubuntu did not do this.  Is it because of some new separation between desktop and server packages?  I installed ssh without issues...


dochood

-----------------------------------------------------------------------------

I got this one fixed.  It was actually a problem with the liblaunchpad-integration package0 / 1 packages.  I did an apt-get update and an apt-get -f install, and it fixed everything.


Doc

---


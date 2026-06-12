---
title: "apt-get extra software issues"
date: 2006-01-14
forum: General Help
---

### Post by klepto on 2006-01-14
Hello,

I've read the man pages on apt-get and I am lost.
When I install some program like snort or acidlab it installs with it a ton
of software that may it may use like apache. When I go to remove snort
and acidlab it doesn't remove the extra software that it installed with it.

Which is wasting precious hard drive space.

/var/cache/apt/archives shows the packages I've installed as of late.
Any way to uninstall them at once?

---

### Post by jasmuz on 2006-01-14
Sure...
sudo apt-get purge package1 package2 package3

the purge option removes even the configuration files

---


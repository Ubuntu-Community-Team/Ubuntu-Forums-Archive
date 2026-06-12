---
title: "aptitude vs adept"
date: 2005-12-13
forum: General Help
---

### Post by skaboss on 2005-12-13
Hello,

Like many other users, i come from my former favourite distro, Debian, and used to perform quite often an "aptitude update", followed by an "aptitude upgrade" to keep my system up to date.
I kept this ritual under my brand new Breezy, and was wondering about the low number of packages to upgrade.
Then i tried adept, and surprise : 42 packages to upgrade !
Why a difference between those 2 methods ?
Ok, that's not blocking, but if someone's got the answer...

---

### Post by Sonicred on 2005-12-13
There is a difference between apt-get upgrade and apt-get dist-upgrade.
dist-upgrade does a better job at resolving dependencies and will also install packages that are being 'held back.' I'm assuming this is what is going on for you.

---

### Post by skaboss on 2005-12-14
I thought that apt-get (or aptitude) dist-upgrade, was only to use for upgrade your kubuntu distro (that's what i used to switch from hoary to breezy), i didn't think you could actually use it to simpy update your packages.
Thanks a lot.

---


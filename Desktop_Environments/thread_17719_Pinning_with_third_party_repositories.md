---
title: "Pinning with third party repositories?"
date: 2005-03-02
forum: Desktop Environments
---

### Post by sard on 2005-03-02
When pinning how can you work out from the url of the repository what should go in the o= and a= sections?


Package: *
Pin: release o= ,a=
Pin-Priority: 300

Also pin-priorities greater than 1000 will be downgraded to, are there any other special numbers?  I wish Debian had decent documentation  :sad: 

Thanks.

---

### Post by farruinn on 2005-03-02
It sounds like you may have already, but if you haven't read [http://www.nl.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-default-version](http://www.nl.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-default-version) and the relevant man page is apt_preferences.

Good luck,
Nathan

---


---
title: "Repository for Knoda?"
date: 2005-06-28
forum: Desktop Environments
---

### Post by scronje on 2005-06-28
I´m new to Ubuntu / Kubuntu, but not to Debian / apt-get. Great distro!!

However, I can´t seem to find an appropriate source to add to my sources list for Knoda. For reference, I include my current configuration below. 

If anyone could point me to an appropriate repository, I would be very greatful.

Steve

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [http://acm.cs.umn.edu/ubp/](http://acm.cs.umn.edu/ubp/) hoary-backports main universe multiverse restricted
deb [http://acm.cs.umn.edu/ubp/](http://acm.cs.umn.edu/ubp/) hoary-extras main universe multiverse restricted

deb [http://kubuntu.org/hoary-kde341](http://kubuntu.org/hoary-kde341) hoary-updates main
deb [http://kubuntu.org/hoary-koffice14](http://kubuntu.org/hoary-koffice14) hoary-updates main

deb [http://debian.neo.pl/wfmh](http://debian.neo.pl/wfmh) unstable main contrib non-free

deb [http://geeksoc.org/~jr/ubuntu/](http://geeksoc.org/~jr/ubuntu/) unstable main

---

### Post by shakin on 2005-06-29
Doesn't look like it's in any repos, but you can install from source using checkinstall in place of the 'make install' command and it will create and install a deb, which can then be managed from synaptic.

---

### Post by scronje on 2005-06-29
[QUOTE=shakin]Doesn't look like it's in any repos, but you can install from source using checkinstall in place of the 'make install' command and it will create and install a deb, which can then be managed from synaptic.[/QUOTE]

Thanks, Shakin, I was just too lazy, I guess  [-X 

I have not used checkinstall, and will look into that as well

---


---
title: "dpkg"
date: 2005-10-18
forum: Desktop Environments
---

### Post by Riverside on 2005-10-18
Am I correct in thinking that dpkg -i is equivalent to rpm -U on systems running the RPM Package Manager, i.e. that dpkg -i will automatically upgrade a previous version of an installed package to a new version?

I have searched these forums and Googled extensively, but the available dpkg documentation does not make this clear.

---

### Post by DJ_Max on 2005-10-18
[QUOTE=Riverside]Am I correct in thinking that dpkg -i is equivalent to rpm -U on systems running the RPM Package Manager, i.e. that dpkg -i will automatically upgrade a previous version of an installed package to a new version?

I have searched these forums and Googled extensively, but the available dpkg documentation does not make this clear.[/QUOTE]
Yes, if a version is already installed, it will attempt to upgrade.

---

### Post by rama on 2005-10-19
So is there a good documentation out there for dpkg? I would like to know exactly how it works.

---

### Post by GrumpyBob on 2005-10-19
Google it!
e.g. [http://www.debian.org/doc/FAQ/ch-pkgtools.en.html](http://www.debian.org/doc/FAQ/ch-pkgtools.en.html)

Robert

---

### Post by rama on 2005-10-19
So how do apt and dpkg relate? If I install a .deb with dpkg will I see it as installed using synaptic?

---


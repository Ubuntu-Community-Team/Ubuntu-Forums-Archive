---
title: "Cannot install programs with APT in Kubuntu 6.06"
date: 2006-07-31
forum: Desktop Environments
---

### Post by spiffytech on 2006-07-31
Today, I tried to install alsa-tools, and now I cannot install anything with APT. When I try to install something (apt-get intall...) , I get this: 

====
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libc6: Depends: tzdata but it is not installable
  libc6-i686: PreDepends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6-15 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

====

And when I try "apt-get -f install", this is what I get: 


====
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libc6: Depends: tzdata but it is not installable
  libc6-i686: PreDepends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6-15 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
====

What can I do to fix my computer?

---

### Post by Ziox on 2006-07-31
perhaps try sudo aptitude install also-tools (or w/e you are trying to install)

---

### Post by Ramses de Norre on 2006-07-31
What's in your sources.list? The ubuntu package for libc6 only depends on locales, as you can see [here]("http://packages.ubuntu.com/dapper/base/libc6").

---

### Post by spiffytech on 2006-08-01
Ziox, your command solved the problem. I can now install software again. Thanks!

---


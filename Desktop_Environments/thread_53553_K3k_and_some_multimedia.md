---
title: "K3k and some multimedia"
date: 2005-08-01
forum: Desktop Environments
---

### Post by ykpaiha on 2005-08-01
I just mentioned looking at kdeapps that the versions I got in my kububtu are far under actual version.

exemple k3b is 11.24 and that one in kdeapps is 12.3 (a substential diff.)

Question: Do i have the right repos or do I have to compile to match my hoary version ?.
(backport enabled)

Thanks

---

### Post by JLTB on 2005-08-02
Hi,

Since ubuntu comes from the sweet OS that is debian you can easily upgrade you whole system using apt.

**WARNING** Updating things in one massive shot can severly screw things up!!! (Although honestly it's only happend to me once in the last 2 years, and the mess up was minor)

do a 'sudo apt-get update' then a 'sudo apt-get dist-upgrade' and apt will get you the newest version of everything out there.

You might want to change your sources file to include restricted, universe, multiverse .. etc to get more stuff.

GL

---


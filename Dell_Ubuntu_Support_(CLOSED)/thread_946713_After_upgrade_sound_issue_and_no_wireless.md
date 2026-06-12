---
title: "After upgrade sound issue and no wireless"
date: 2008-10-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lavarock on 2008-10-13
Hi, I have been using ubuntu for a year and half.  I am using Hardy Heron.  My laptop is a XPS M1210.  

Today I upgraded lots of packages.  In fact I performed two upgrades, and after the second upgrade stuff started to not work.  (I am sure that the first upgrade everything was alright.)  

The problem is that my speaker start to make beep sound when I try auto-complete in terminal, and wireless stopped working.

I had the same thing happened before, and I think the problem is with this package linux-restricted-modules-2.6.24-19-generic.  Last time I was able to single out the problem since I only upgrade this package and it produced this exact same problem.  This time I am not sure since the second upgrade was upgrading 25 packages.  What can I do to fix this problem? Thanks!

To be precise, this is the install log for the upgrade
```
Upgraded the following packages:
bind9-host (1:9.4.2-10) to 1:9.4.2-10ubuntu0.1
dnsutils (1:9.4.2-10) to 1:9.4.2-10ubuntu0.1
f-spot (0.4.2-1ubuntu3) to 0.4.3.1-0ubuntu1
language-support-writing-en (1:8.04+20080410) to 1:8.04+20080630
libbind9-30 (1:9.4.2-10) to 1:9.4.2-10ubuntu0.1
libisccfg30 (1:9.4.2-10) to 1:9.4.2-10ubuntu0.1
linux-backports-modules-hardy-generic (2.6.24.16.18) to 2.6.24.19.21
linux-headers-generic (2.6.24.16.18) to 2.6.24.19.21
linux-restricted-modules-generic (2.6.24.16.18) to 2.6.24.19.21
openjdk-6-jre (6b09-0ubuntu2) to 6b11-2ubuntu2
openjdk-6-jre-headless (6b09-0ubuntu2) to 6b11-2ubuntu2
openjdk-6-jre-lib (6b09-0ubuntu2) to 6b11-2ubuntu2
ssl-cert (1.0.14-0ubuntu2) to 1.0.14-0ubuntu2.1
wine (0.9.59-0ubuntu4) to 1.0.0-1ubuntu4~hardy1
```

---


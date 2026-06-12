---
title: "SVG in Firefox"
date: 2005-01-29
forum: Desktop Environments
---

### Post by celloandy on 2005-01-29
I moved to Ubuntu from Gentoo, and have been really happy with it, but I was wondering how to get SVG support for Firefox.  In gentoo, it was a matter of compiling it using "USE='svg' emerge mozilla-firefox," but the default build in the Ubuntu repositories doesn't have support for svg built in.  I'm also aware that there's an Adobe viewer that's pretty popular as an alternative to the native support, but all that's available on the site is an RPM.

Basically, I'm perfectly capable of either compiling my own firefox or rpm2tgz'ing the Adobe package and hand-installing it, but I was wondering if there was a more kosher, Ubuntu way of solving this problem.

Andrew

---

### Post by wiscalico on 2005-01-30
Try to take a look at apt-get source which downloads the source for a package. You should then be able to do the same trick as on Gentoo (USE=svg) and make your own deb-package with the tool dpkg-buildpackage.

I might not have all the details correct but I hope this leads you in the right direction.

---


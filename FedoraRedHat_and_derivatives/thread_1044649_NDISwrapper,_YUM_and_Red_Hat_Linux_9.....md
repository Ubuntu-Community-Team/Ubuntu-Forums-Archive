---
title: "NDISwrapper, YUM and Red Hat Linux 9...."
date: 2009-01-19
forum: Fedora/RedHat and derivatives
---

### Post by icanfly0307 on 2009-01-19
Hi all,
       I was checking for a fast linux distro to use on my 256MB RAM, 1GHz Pentium 3 computer and I unearthed a Red Hat 9 CD in my basement. Believe it or not, I decided to install it (RHL 9 was obsoleted in 2003) :grin:. The only issue I have is installing ndiswrapper. Are there precompiled binaries for NDISwrapper in RHL 9? Also, is it possible to install YUM in RHL 9? Thanks for your help... :)

---

### Post by igknighted on 2009-01-19
Red Hat 9 shipped with a 2.4 series kernel.  I'm 99% sure that ndiswrapper needs a 2.6 series kernel.  You could try to compile a new kernel yourself, but I would imagine this would be a non-trivial process.  I wouldn't hold my breath on Yum either.  It is designed for a new version of rpm, so I'm not sure it would work with the old version.

---


---
title: "&quot;python3&quot; or &quot;python3.0&quot;?"
date: 2009-06-16
forum: General Help
---

### Post by lanec42 on 2009-06-16
I'm learning python, and the documentation on Python's site ([http://docs.python.org/3.0/tutorial/interpreter.html#id2](http://docs.python.org/3.0/tutorial/interpreter.html#id2)) says that the python interpreter is named "python3.0". However, apt is showing me a "python3" package as well.

What is the difference between these two packages, and which should I use?
Thanks.

---

### Post by ad_267 on 2009-06-16
```
apt-cache show python3
Package: python3
Priority: optional
Section: universe/python
Installed-Size: 76
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Matthias Klose <doko@debian.org>
Architecture: all
Source: python3-defaults
Version: 3.0.1-0ubuntu4
Depends: **python3.0** (>= 3.0.1), python3-minimal (= 3.0.1-0ubuntu4)
Suggests: python3-doc (>= 3.0.1-0ubuntu4), python3-tk (>= 3.0.1-0ubuntu4), python3-profiler (>= 3.0.1-0ubuntu4)
Filename: pool/universe/p/python3-defaults/python3_3.0.1-0ubuntu4_all.deb
Size: 11014
MD5sum: 0904f81f97a4baba5d642778ed61bbee
SHA1: 8f9f20727d1144a0d11fa74bef7fd4f889da9ae4
SHA256: f7a25c3df43e146180c5038fd1bcc5d3e6159a23fe8ef042cbd051986bcef485
Description: An interactive high-level object-oriented language (default python3 version)
 Python, the high-level, interactive object oriented language,
 includes an extensive class library with lots of goodies for
 network programming, system administration, sounds and graphics.
 .
 This package is a dependency package, which depends on Debian's default
 Python version (currently v3.0).
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
```

The python3 package will install python3.0

---

### Post by lanec42 on 2009-06-17
Great, thanks a lot! I need to learn some more about apt...

---

### Post by ad_267 on 2009-06-17
> **lanec42 said:**
> Great, thanks a lot! I need to learn some more about apt...

Cheers, you should be able to find that same information in Synaptic too.

---


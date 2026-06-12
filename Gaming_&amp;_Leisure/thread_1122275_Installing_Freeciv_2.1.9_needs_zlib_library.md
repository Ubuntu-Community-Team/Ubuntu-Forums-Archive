---
title: "Installing Freeciv 2.1.9: needs zlib library?"
date: 2009-04-10
forum: Gaming &amp; Leisure
---

### Post by The Question on 2009-04-10
Hello,

I am trying to install Freeciv 2.1.9 from the zip.  When I run configure, I get an error message of "Could not find zlib library."  I installed a few zlib packages with Synaptic (zlibc and zlibbin) but that did not solve it.
How do I install the zlib library?

Why is Ubuntu lagging behind with Freeciv?  Only version 2.1.5 is available with Add/Remove.

Thanks.

---

### Post by Perfect Storm on 2009-04-11
```
sudo apt-get install zlib1g-dev
```

Should do it.

---

### Post by The Question on 2009-04-13
Thanks, that worked.  I abandoned trying to install gtk client however, since I was getting other missing components with no clear idea of which packages to install.  And SDL looked much easier.

So anyway, got everything compiled and installed.  But now it just won't work.  Executables are right there, but entering civserver and civclient tell me those programs are not installed and I can get them by sudo apt-get install etc. which will just get me 2.1.5 again.

It seems Ubuntu just does not know they are there because I didn't install the packages.

---

### Post by Neheb on 2009-04-13
If you have just unpacked it from an archive I think you have to specify what executable (with path) it is you want to run, not just say the name of it.

at least that is what I had to do when getting robocode from a zip file instead of trough the manager,

---

### Post by The Question on 2009-04-14
Thanks, it works now. =)  Note to self: BASH does not equal MS-DOS.

---


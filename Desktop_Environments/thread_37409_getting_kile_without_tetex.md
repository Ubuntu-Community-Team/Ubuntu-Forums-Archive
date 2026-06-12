---
title: "getting kile without tetex"
date: 2005-05-27
forum: Desktop Environments
---

### Post by Neil Leslie on 2005-05-27
Hi,
Since   have a perfectly good complete tex installation from TeXLive 2004 , I want to install kile *without* installing tetex.  Is there a way I can tell the package manager to ignore tetex when installing kile? Surely kile doesn't *really* depend on tetex, but on a tex being available?

Cheers,
Neil

---

### Post by MikeMay on 2005-08-10
Here is the kile_1.6.3-1.dsc File:

Kile does not depend on any latex installation ... so I guess you can just install it...

-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA1

Format: 1.0
Source: kile
Version: 1:1.6.3-1
Binary: kile, ktexmaker2
Maintainer: Ben Burton <bab@debian.org>
Architecture: any
Standards-Version: 3.6.1
Build-Depends: debhelper (>> 4.0.0), kdelibs4-dev (>> 4:3.2.0), libqt3-compat-headers, libqt3-mt-dev (>= 3:3.2.1)
Files: 
 9fd14182468ccd08f2fe4ae54163d976 2195090 kile_1.6.3.orig.tar.gz
 362006cc882f0260eb123a8db5d4f755 42781 kile_1.6.3-1.diff.gz

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.2.4 (GNU/Linux)

iD8DBQFA1Ve6MQNuxza4YcERArxfAJwI3iAfywHcef7D1VQAj7NJrgPeqgCffKQn
DlwpOxC1BWBwDobVj27mcQA=
=11FS
-----END PGP SIGNATURE-----

---

### Post by neoflight on 2006-01-08
But how? and how do u tell kile to use the texlive installation.? any path to give?
thanks

---

### Post by Neil Leslie on 2006-01-08
When I upgraded to 5.10 I ended up just getting the kile sources and compliling it, hence avoiding the package manager. IIRC compilation worked fine, after a bit of fiddling to get the correct gcc to be used.

The kile *package* depends on tetex-bin, and synaptic (or other package managers) will insist on going off and getting tetex-bin and installing it.  This is a mistake, as tetex-bin should only be like a dvi reader and a ps or pdf reader and be recommended. If you want tetex-bin (and many people will) then the package manager should help you to get it, but if you don't want it then having another tex downloaded and installed is not useful.

All the helper programs for kile (tex, latex, pdflatex, bibtex, a dvi reader, a ps reader, pdf reader etc) are specified in settings/configure/build. But if these are on your current path then the default should work.

Good luck,
Neil

---


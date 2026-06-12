---
title: "Libraries on Ubuntu -- will source code versions work?"
date: 2006-08-24
forum: Desktop Environments
---

### Post by ChantCd_com on 2006-08-24
Look at this page, at the very bottom:

[http://packages.ubuntu.com/dapper/libs/libgcc1](http://packages.ubuntu.com/dapper/libs/libgcc1)

-------------------------------------
Source Package: gcc-4.0, Download: [dsc] [gcc-4.0_4.0.3.orig.tar.gz] [gcc-4.0_4.0.3-1ubuntu5.diff.gz] 
--------------------------------------

Now can I install ANY SOURCE I find, knowing that it will compile for my system and will work -- or do I have to restrict myself to Ubuntu-ized versions of all the various packages?

Also, do I need to update the source code with the gcc-4.0_4.0.3-1ubuntu5.diff.gz package, or will the "original" source code work on my system?

This is a stupid question, but I can't find the answer anywhere.

I HAVE had problems (just yesterday) with installing .DEB packages that weren't Ubuntu. I learned that the hard way -- had to wipe my system! Now I'm installing everything from source or from APT-GET. I'm no longer using the dpkg utility to install .DEB packages I found somewhere on the Net (usually for Debian Linux, not Ubuntu)

Any help would be appreciated.

Thanks,

Matthew


The "Debian changelog" says:

gcc-4.0 (4.0.3-1ubuntu5) dapper; urgency=low

* sparc-update: config/sparc/sparc.c (emit_and_preserve): Allocate space
for the register save area. Taken from the gcc-4_0-branch.
* hppa-cbranch, hppa-cbranch2 patches: Fix for PR target/26743,
PR target/11254, PR target/10274, backport from trunk (Randolph Chung).
* Fix PR c++/10385, PR c++/26036, PR c++/26558, ICE's on invalid code,
taken from the gcc-4_0-branch.

-- Matthias Klose <doko@ubuntu.com> Thu, 20 Apr 2006 18:27:33 +0200

gcc-4.0 (4.0.3-1ubuntu4) dapper; urgency=low

* PR middle-end/20297, taken from the gcc-4_0-branch.
* Fix PR target/25917, ia64, 4.0/4.1 regression, assemble-failure.
* Keep libffi doc files in its own directory.
* Stop building the libffi4* packages from the gcc-4.0 source.

-- Matthias Klose <doko@ubuntu.com> Sat, 8 Apr 2006 01:23:46 +0200

gcc-4.0 (4.0.3-1ubuntu3) dapper; urgency=low

* PR middle-end/26379 (ice-on-vaild-code, regression), taken from
the gcc-4_0-branch.
* PR middle-end/26557 (ice-on-vaild-code, regression), taken from
the gcc-4_0-branch. Closes: #349083.
* Stop building fastjar from the gcc-4.0 source.

-- Matthias Klose <doko@ubuntu.com> Sun, 19 Mar 2006 12:18:37 +0100

---


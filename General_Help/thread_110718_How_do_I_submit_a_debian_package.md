---
title: "How do I submit a debian package?"
date: 2005-12-31
forum: General Help
---

### Post by wgscott on 2005-12-31
The blt debian package, both on Ubuntu and upstream, is broken.  It arbitrarily eliminates the /usr/bin/bltwish binary that gets installed by default when one compiles and installs bltwish from the sourcecode.

I wrote to the maintainer, and was dismissed with the explanation that bltwish really isn't needed.

The problem is that it IS needed by [at least some popular pieces of software that depend on blt](http://www.google.com/search?client=safari&rls=en&q=bltwish&ie=UTF-8&oe=UTF-8).  If configure doesn't find /usr/bin/bltwish or /usr/local/bltwish, it fails.

Since I was unable to convince anyone that a 933Kb executable that gets installed by default should in fact be included in the blt package (and therefore the default ubuntu distribution), I rolled by own subsidiary debian package, bltwish, that installs this one additional 933Kb file.

[bltwish-2.4z-unofficial_i386.deb](http://xanana.ucsc.edu/linux/deb/bltwish-2.4z-unofficial_i386.deb)

It would be nice if Ubuntu users at least had the option of installing this if they need to compile software that depends on its presence.  Given that pretty much everything else compiles "out of the box" on Ubuntu, it seems a bit silly not to give users at least the option of an unbroken blt installation.  

I understand it is a debian linux problem rather than specifically an ubuntu problem, but it is pretty easy to fix...

---

### Post by az on 2005-12-31
From the blt changelog:
 (2.4j-1) unstable; urgency=low
* bltwish now does not exist. Better to use wish, and then
     package require BLT (saves 610KBytes).

[http://packages.ubuntu.com/changelogs/pool/main/b/blt/blt_2.4z-3ubuntu1/changelog](http://packages.ubuntu.com/changelogs/pool/main/b/blt/blt_2.4z-3ubuntu1/changelog)


I guess it means that wish is preferred over an obsolete bltwish.  usr/bin/wish8.4	is provided by tk8.4.  Is there supposed to be a symlink to make wish use that?  (or bltwish?)

But, to answer your question, you either have to convince the debian maintainer than the problem needs fixing (making an ancillary package would be the way to go, I guess).  You can try to convince someone in MOTU (Masters of the universe - they maintain all of the packages in universe) to make a package for bltwish.

If you want to join MOTU, check out their wiki page and dive in.

---

### Post by wgscott on 2005-12-31
Thanks for replying.  That was the answer they gave me.  bltwish is different, but you can use wish and then import blt into it.  

That's fine if you are writing the code, but if your main concern is using what is already out there, then configure scripts that expect to find a bltwish binary and don't will still fail.  

If the main concern is making the ubuntu platform usable, rather than ideologically pure, it seems like a small price to pay.

---


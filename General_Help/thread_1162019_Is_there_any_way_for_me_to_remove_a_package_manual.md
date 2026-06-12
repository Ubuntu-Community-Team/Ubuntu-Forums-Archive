---
title: "Is there any way for me to remove a package manually?"
date: 2009-05-17
forum: General Help
---

### Post by DiscipleRayne on 2009-05-17
I installed ghc6 and gtk2hs along the way, and GHC is working fine, but for some reason libghc6-cairo-dev and libghc6-glib-dev was giving me trouble, so I tried to remove them completely. libghc6-cairo-dev removed itself perfectly, with no problems. When I tried to remove libghc6-glib-dev, I keep getting this:

```
The following packages will be REMOVED:
  libghc6-glib-dev
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1372kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 141061 files and directories currently installed.)
Removing libghc6-glib-dev ...
ghc-pkg: cannot find package glib-0.9.12.1
dpkg: error processing libghc6-glib-dev (--remove):
 subprocess pre-removal script returned error exit status 1
Reading package info from "/usr/lib/haskell-packages/ghc6/lib/glib-0.9.12.1/glib.package.conf" ... done.
ghc-pkg: Unversioned dependencies found: base
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 libghc6-glib-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I don't know what to do, I've tried everything. Is there anyway I can just remove this package myself, manually? It keeps trying to install it everytime I install new packages and it always errors out. Please help, I'm terribly frustrated.

---

### Post by mb_webguy on 2009-05-17
Have you tried reinstalling the package, then removing it?

---


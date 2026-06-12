---
title: "Having trouble with LXDream 0.8.4"
date: 2008-08-24
forum: Gaming &amp; Leisure
---

### Post by lxdreamn00b on 2008-08-24
System specs:
Ubuntu 8.04
Graphics card - ATI Technologies Inc RV280 [Radeon 9200] (rev 01)
Sound card - Intel ICH5 with AD1981B

I've downloaded the .deb release of lxdream 0.8.4, but now when I go to open the package with GDebi, it won't let me install it and the status will say **'Error: Dependency is not satisfiable: libasound2'**. Which doesn't make sense, since Synaptic says I already have libasound2 installed.

When I try to install the tar.gz of the lxdream 0.8.4 build, I get:
```
checking for LIBPNG... configure: error: Package requirements (libpng ) were not met:

No package 'libpng' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBPNG_CFLAGS
and LIBPNG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

Also, the reason I posted my system specs is to see if I should even bother with getting it to run, I've tried nullDC 1.0.3 with WINE, which runs fine but the gameplay is way too slow.

Thanks.

---

### Post by GSZX1337 on 2008-08-24
Have you tried using [getlibs]("http://ubuntuforums.org/showthread.php?t=474790")?

---


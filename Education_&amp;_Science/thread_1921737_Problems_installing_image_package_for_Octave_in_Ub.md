---
title: "Problems installing image package for Octave in Ubuntu"
date: 2012-02-07
forum: Education &amp; Science
---

### Post by skytreader on 2012-02-07
I'm trying to install the image package 1.0.15 in Octave 3.2.3 under Ubuntu. However, when I try to install, it runs fine for a few moments then stumbles into this error:

```

octave3.2:1> pkg install image-1.0.15.tar.gz
__boundary__.cc:24:31: error: octave/oct-locbuf.h: No such file or directory
make: *** [__boundary__.oct] Error 1
'make' returned the following error: make: Entering directory `/tmp/oct-WAPcqr/image-1.0.15/src'
mkoctfile -Wall __spatial_filtering__.cc
mkoctfile -Wall __bilateral__.cc
mkoctfile -Wall __custom_gaussian_smoothing__.cc
mkoctfile -Wall __boundary__.cc
make: Leaving directory `/tmp/oct-WAPcqr/image-1.0.15/src'
error: called from `pkg>configure_make' in file /usr/share/octave/3.2.3/m/pkg/pkg.m near line 1253, column 2
error: called from:
error:   /usr/share/octave/3.2.3/m/pkg/pkg.m at line 714, column 5
error:   /usr/share/octave/3.2.3/m/pkg/pkg.m at line 287, column 7

```

How can I get around this? Thank you!

---


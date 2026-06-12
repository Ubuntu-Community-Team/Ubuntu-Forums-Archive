---
title: "Installing from source with libtiff3/libtiff4"
date: 2005-12-15
forum: Desktop Environments
---

### Post by Niall Flinn on 2005-12-15
Hi folks,

I'm trying to install the latest version of Cinepaint (0.20-1). I'm attempting to install it from source, since there isn't a debian release yet. The main problem I'm having is that it requires libtiff3-dev, which is no longer part of Ubuntu, as libtiff3 has apparently been superceded by libtiff4. Is it possible to have both versions coexisting, or alternatively, how can I alter the contents of the source package to use libtiff4 instead?

Thanks,

Niall

---

### Post by stuporglue on 2005-12-15
I don't plan on doing this myself, so I can't give you a step by step, but here's the gist of it:

What you'll need to do is when running ./configure on libtiff, check the configure options, and install libtiff3 to somewhere where libtiff4 isn't. You can probably see the configure options by running ./configure --help. 

That will compile libtiff and install it outside the normal library search path, so when you go to ./configure cinepaint, you'll need to check it's configure options and add the path where libtiff3 got installed to it's library search path. 

If cinepaint complains that it can't find other libraries, you'll need to have both paths in the lib search path, but with the libtiff4 path first.

---

### Post by Niall Flinn on 2005-12-15
OK, looks like I didn't need to do anything to use libtiff4 - I've managed to compile cinepaint without errors, but now, when I run it, it can't see any of the plugins it needs to read (for example) tiff files. I assume this is because they aren't in the expected directories. Is there any way of knowing where all this stuff needs to go in my system?

Thanks,

Niall

---


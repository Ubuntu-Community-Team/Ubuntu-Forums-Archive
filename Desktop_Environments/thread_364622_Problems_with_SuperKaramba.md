---
title: "Problems with SuperKaramba"
date: 2007-02-18
forum: Desktop Environments
---

### Post by shinda on 2007-02-18
I've tried installing superkarmba through synpatic but was having a few different problems so I thought I'd try compiling it from source. When I run the ./configure though I'm told I'm missing several Python libraries, (maybe thats why it wasn't working in the first place). Anyways when I checked snypatic it looks like I got all the main python packages installed.

I even tried running ```
sudo apt-get install python2.4
``` and am told that that is all there and nothing needs to be done.

The exact error I get from the configure is as follows, can anyone direct me as to which packages I may be missing and need to install?

```
checking for Python directory... /usr/local
checking for Python2.4... header no library no modules /usr/lib/python2.4
checking for Python2.3... header no library no modules no
checking for Python2.2... header no library no modules no
checking for Python2.1... header no library no modules no
checking for Python2.0... header no library no modules no
checking for Python1.5... header no library no modules no
checking for libxmms... ./configure: line 43081: xmms-config: command not found
./configure: line 43083: xmms-config: command not found
no
checking for main in -lknewstuff... yes
checking for main in -lkvm... no
checking if doc should be compiled... yes
checking if superkaramba should be compiled... no
configure: creating ./config.status
fast creating Makefile
fast creating doc/Makefile
fast creating doc/superkaramba/Makefile
fast creating superkaramba/Makefile
fast creating superkaramba/doc/Makefile
fast creating superkaramba/icons/Makefile
fast creating superkaramba/mimetypes/Makefile
fast creating superkaramba/src/Makefile
config.pl: fast created 8 file(s).
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

Superkaramba can't be compiled
because of missing Python libraries/headers.
```

Thanks in advance

---

### Post by shinda on 2007-02-19
Well looks like it was the Python libraries. I updated by installing PyGTK and also imagemagick and things seem good to go now.

---


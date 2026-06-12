---
title: "Beagle (mono?) complaints about corlib version"
date: 2006-05-31
forum: Desktop Environments
---

### Post by mcguin on 2006-05-31
When I run any beagle application (i.e. beagle-info) I get: 

Corlib not in sync with this runtime: expected corlib version 46, found 47.
Download a newer corlib or a newer runtime at [http://www.go-mono.com/daily]("http://www.go-mono.com/daily").

I have installed:

beagle 0.2.6-1ubuntu5
libbeagle0 0.2.6-1ubuntu5
libmono0 1.1.13.6-0ubuntu3
mono-classlib-1.0 1.1.13.6-0ubuntu3
mono-common 1.1.13.6-0ubuntu3
mono-jit 1.1.13.6-0ubuntu3

The system has been upgraded from breezy.

---

### Post by mcguin on 2006-05-31
Ok, solved. I have unset MONO_PATH and now is working. Thanks.

---


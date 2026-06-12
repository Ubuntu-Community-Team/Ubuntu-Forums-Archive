---
title: "Totem 2.x on Dapper"
date: 2006-12-07
forum: Desktop Environments
---

### Post by jazzgossen on 2006-12-07
Is it possible to run the latest (edgy) version of Totem on Dapper? I couldn't find anything in the backports repo's. 

I tried to compile Totem 2.17 from source, but when configuring, it complains that 

checking for NVTV... checking for XINE... checking for backend libraries... checking for GST... configure: error: you need the GStreamer or the xine-lib development packages installed

even though I do have libgstreamer0.10-dev and libgstreamer-plugins-base0.10-dev installed. Is there another GStreamer development package?

---

### Post by majoridiot on 2006-12-08
try:

```
sudo apt-get install xine-lib-dev
```

and the compile.  please post your progress, as i intend to upgrade
totem myself.

---

### Post by jazzgossen on 2006-12-09
I couldn't find a xine-lib-dev package, but I installed libxine-dev. I still get the same configure error, though.

---

### Post by majoridiot on 2006-12-09
sorry for the total buggering up of that one...

i don't see any other dev packages that look applicable, either.

---


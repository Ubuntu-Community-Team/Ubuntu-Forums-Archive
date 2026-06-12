---
title: "sound delay in firefox flash"
date: 2005-11-30
forum: Desktop Environments
---

### Post by dr.drake on 2005-11-30
anybody else got this problem?
but more importantly: how do I fix this?
it's really starating to bug me, and I can't be the only one having this problem, can I?

thanks,

---

### Post by Eversmann on 2005-11-30
I also have it on some sites using flash for videos, like youtube and metacafe.

---

### Post by dr.drake on 2005-12-23
<BUMP> ;) 

(it's driving me nuts, so many sites nowadays use flash animation, and when the sound comes a full second after the image, it's virtually unwatchable for me)

---

### Post by rikai on 2005-12-23
have you tried following the [flash sound issues section]("https://wiki.ubuntu.com/RestrictedFormats#head-832969c4301548599ecbe6393e2682a4e343af67") of the restricted format wiki page?

Let us know if it works.

---

### Post by dr.drake on 2005-12-27
ok, just tried the options, but 'no, nada, nothing'...

the first option left me with no sound at all:

```
Open:

gedit ~/.mozilla/firefox/rc

Add the line:

FIREFOX_DSP="none"

```

the second one just gave me: ln: `/usr/lib/libesd.so.1': File exists

and since I'm not on an AMD64 or PPC, so I didn't try to install gplflash or swfdec (yet).

so, still stuck with an annoying sound delay... :(

---


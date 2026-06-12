---
title: "mplayer problems"
date: 2006-04-16
forum: Desktop Environments
---

### Post by theredcross on 2006-04-16
i'm compiling mplayer from source, to get the extra codecs installed, and i ran into a problem shortly after ./configure. 
```
'make' will now compile MPlayer and 'make install' will install it.
Note: On non-Linux systems you might need to use 'gmake' instead of 'make'.

Please check mtrr settings at /proc/mtrr (see DOCS/HTML/en/video.html#mtrr)


Check configure.log if you wonder why an autodetection failed (check whether
the development headers/packages are installed).

If you suspect a bug, please read DOCS/HTML/en/bugreports.html.

root@HEMI:/home/tim/MPlayer-1.0pre7try2# make
bash: make: command not found

```
i have no idea what to do about that, nor do I see anything out of the ordinary. tried gmake just in case, no dice either.

---

### Post by bscbrit on 2006-04-16
Wouldn't it be _much_ easier simply to install the w32codecs?

However, your problem is caused by the missing utilities, which can be installed using Synaptic or apt-get.  They are called 'build-essential'.  I still don't think it is worth the effort just to install the codecs that are already available in an Ubuntu package though.

---


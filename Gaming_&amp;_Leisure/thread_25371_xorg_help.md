---
title: "xorg help?"
date: 2005-04-10
forum: Gaming &amp; Leisure
---

### Post by hunham on 2005-04-10
Hi,
I've recently switched to Ubuntu (it's great!) and I'm trying to compile my SDL-based game on it. SDL requires a bunch of X libs, one of which is Xmu. ./configure only worked after I added this symlink:

/usr/X11R6/lib/libXmu.so -> /usr/X11R6/lib/libXmu.so.6

Did anyone else experience this? Is this an oversight by x.org or ubuntu, or is my configure script bad? (I'm using a pretty standard one to detect SDL, SDL_mixer, etc.)

Thanks for any info!

---

### Post by Nis on 2005-04-10
Looks like a packaging oversight.  I wouldn't worry too much about it if you got it working.  You might want to file a bug report though (for Ubuntu, not SDL or Xorg).

---


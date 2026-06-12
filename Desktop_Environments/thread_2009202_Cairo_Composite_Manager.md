---
title: "Cairo Composite Manager"
date: 2012-06-24
forum: Desktop Environments
---

### Post by mrfreen on 2012-06-24
Has anyone managed to get Cairo Composite Manager working under Ubuntu 12.04? 

I'm currently using a combo of openbox, cairo-dock and xcompmgr and it's great, except xcompmgr sometimes crashes, causing x to restart. Apparently it's no longer maintained, so I looked for an alternative.

I found this:
[http://cairo-compmgr.tuxfamily.org](http://cairo-compmgr.tuxfamily.org)
but there are no Ubuntu packages available, the debian packages don't work and I can't seem to compile it from source.

Has anyone had any luck getting this working, or have you any alternatives for a lightweight, stable composite manager?

---

### Post by zombifier25 on 2012-06-24
I doubt it will work also, because the latest release is in 2010.

---

### Post by mrfreen on 2012-06-24
Yeah, I managed to compile it, and now I've got it running (sort of) there's black boxes around everything and slow performance.

*sigh*
Back to to the buggy segfaulting xcompmgr I guess...

(at least it's better than gnome 3 and unity)

---

### Post by mrfreen on 2012-06-24
UPDATE: I just found that xcompmgr is now defunct and has been replaced by "Compton", which can be found at:
[https://github.com/chjj/compton](https://github.com/chjj/compton)

You have to install from source, but on 12.04 it compiles without problems and seems a lot more stable and light than xcompmgr.

I wonder why this isn't in the repositories, but the buggy, unsupported xcompmgr is?

---


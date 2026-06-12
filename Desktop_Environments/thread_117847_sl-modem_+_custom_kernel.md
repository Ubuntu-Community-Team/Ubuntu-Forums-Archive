---
title: "sl-modem + custom kernel"
date: 2006-01-15
forum: Desktop Environments
---

### Post by BrianB on 2006-01-15
I've compiled my own custom kernel and everything is just dandy:) except I can't get the slmodem modules to work. I can build them by hand i.e. make; make install and slamr is loaded at boot but the /dev/modem symlink doesn't work. I can't dialout and haven't a clue what's wrong?

---

### Post by pkoufalas on 2006-01-15
I remember I had to only build from source for part of this, sl-modem-modules I think...the source code was available from the repos and I built the deb package from it for my particular kernel (686-smp).

Not sure what you mean by /dev/modem symlink doesn't work. So it's there? It points to ...? I may have had to manually create one.

Have a look at your /etc/default/sl-modem config file or in /etc/init.d/sl-modem-daemon (or whatever it's called). It may be setup to use ALSA by default.

What group is it running as? Dialout? You may need to add yourself to that group.

Hope this helps.

---


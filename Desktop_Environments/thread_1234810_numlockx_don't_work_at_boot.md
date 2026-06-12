---
title: "numlockx don't work at boot"
date: 2009-08-08
forum: Desktop Environments
---

### Post by kapetr on 2009-08-08
Hello

The problem is, then numlockx has no effect by start of system.

I have tested, that the /etc/X11/Xsession.d/55numlockx is called by start of X, but without effect.

I I run it manually after login, it work normally.

It s not great, but poisoning Problem :-/

Any idea ?

Thanks

Ubuntu 9.04

---

### Post by kapetr on 2009-08-20
Hello 

I HACKED this:

I had add to the end of/etc/gdm/Init/Default :

if [ -x /usr/bin/numlockx ]; then
  /usr/bin/numlockx on
fi

It works.

P.S.: As I have find out, the /etc/X11/Xsession.d/55numlockx is working, but  unfortunately too late - after GDM login. Also - by typing my password, I had to press NumLock key.
But with this my hack is it now not necessary.

---


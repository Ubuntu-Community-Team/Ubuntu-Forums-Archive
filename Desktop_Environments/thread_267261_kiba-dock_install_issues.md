---
title: "kiba-dock install issues"
date: 2006-09-28
forum: Desktop Environments
---

### Post by Nycthbris on 2006-09-28
I am following this howto ([http://fredcpp.wordpress.com/2006/09/03/install-kiba-dock-in-xgl-compiz/]("http://fredcpp.wordpress.com/2006/09/03/install-kiba-dock-in-xgl-compiz/") ) to install kiba dock. I had to downgrade libcairo2 in order to satisfy some dependencies. When I get to the step with ./autogen.sh this is what it spits out
```

xxx@xxxxx:~/kiba-dock$ ./autogen.sh
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal  --output=aclocal.m4t
autoreconf: `aclocal.m4' is unchanged
autoreconf: configure.in: tracing
autoreconf: configure.in: not using Libtool
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy
configure.in: 8: required file `./[config.h].in' not found
akamaru/Makefile.am:7: variable `GTK_LIBS' not defined
akamaru/Makefile.am:7: variable `CAIRO_LIBS' not defined
files/Makefile.am:9: variable `glade_DATA' not defined
autoreconf: automake failed with exit status: 1
xxx@xxxxx:~/kiba-dock$


```

Any help would be great! Thanks!

---

### Post by mjpoetic on 2006-10-02
I am having the same problem right now trying to install it that way.  The funny thing is I didn't have this problem before when I installed it on this very laptop.  I recently reinstalled dapper (trying to do a fresh start with my desktop) and now it seems I can't get kiba-dock going.  Anyway, if you want...you can try this kiba-dock deb package I found in a post....feel free to see if it works on your system.  I can make no guarantees though.  I have zipped it for you below.

p.s.
You can always try this page for another way to install:
[http://www.ubuntuforums.org/showthread.php?t=235643](http://www.ubuntuforums.org/showthread.php?t=235643)

p.p.s.
After installing the deb package...run **kiba-systray.py** for kiba-dock and the system tray icon.

---

### Post by distroman on 2006-10-02
Seems that you need to upgrade your automake to edgy. 
Works here, but well, no guarantees.
[https://launchpad.net/distros/ubuntu/edgy/i386/automake1.9/1.9.6-4](https://launchpad.net/distros/ubuntu/edgy/i386/automake1.9/1.9.6-4)
Also go here for a more up-to-date howto.
[http://forum.beryl-project.org/index.html](http://forum.beryl-project.org/index.html)

---

### Post by mjpoetic on 2006-10-03
This most certainly did the trick :)  Thanks distroman...you're my hero!

---


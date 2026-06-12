---
title: "compiz and emerald in flashback Ubuntu 16.04"
date: 2018-01-19
forum: Desktop Environments
---

### Post by fattyz on 2018-01-19
Hi I have installed Ubuntu 16.04 (several times in the last few days) and now when I install gnome-session-flashback, I can't install emerald.  I can't do anything in fact, install or un install but I get this.

The following packages have unmet dependencies:
 emerald:i386 : Depends: compiz-plugins:i386 but it is not going to be installed
                Depends: libdecoration0:i386 (>= 1:0.9.7.0~bzr2995) but it is not going to be installed
                Depends: libc6:i386 (>= 2.4) but it is not going to be installed
                Depends: libcairo2:i386 (>= 1.2.4) but it is not going to be installed
                Depends: libgdk-pixbuf2.0-0:i386 (>= 2.22.0) but it is not going to be installed
                Depends: libglib2.0-0:i386 (>= 2.35.9) but it is not going to be installed
                Depends: libgtk2.0-0:i386 (>= 2.24.0) but it is not going to be installed
                Depends: libpango-1.0-0:i386 (>= 1.14.0) but it is not going to be installed
                Depends: libpangocairo-1.0-0:i386 (>= 1.14.0) but it is not going to be installed
                Depends: libwnck22:i386 (>= 1:2.22) but it is not going to be installed
                Depends: libx11-6:i386 but it is not going to be installed
                Depends: libxrender1:i386 but it is not going to be installed
                Recommends: emerald-themes:i386 but it is not installable
 libemeraldengine0:i386 : Depends: libc6:i386 (>= 2.4) but it is not going to be installed
                          Depends: libcairo2:i386 (>= 1.2.4) but it is not going to be installed
                          Depends: libgdk-pixbuf2.0-0:i386 (>= 2.22.0) but it is not going to be installed
                          Depends: libglib2.0-0:i386 (>= 2.35.9) but it is not going to be installed
                          Depends: libgtk2.0-0:i386 (>= 2.8.0) but it is not going to be installed
                          Depends: libpango-1.0-0:i386 (>= 1.14.0) but it is not going to be installed
                          Depends: libx11-6:i386 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution)

It looks to me like it didn't install correctly?  Compiz is working and seems 3d because I get the cube and deformation, but seems like a lot of the stuff it depends on is missing?
I reinstalled several times.  Compiz is working, I assume there is some kind of 3d because I get the cube.  Emerald actually installed and is on but generates an error on launching.

Failed to execute child process "emerald-theme-manager" (No such file or directory)

Oh it works BTW I've had it going a couple times already.  : )  I'm just not wanting to reinstall (I don't know really what happened) but you get used to re-installing it's not that bad.  lol


Thanks

---

### Post by fattyz on 2018-01-20
Hi after reading some more it seems like python and lots of other things are missing?  IDK what happened.  Time to re install again I guess.  Oh well!

Thanks better luck this time!

---

### Post by Frogs Hair on 2018-01-20
Emerald PPA

[https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8/+index?batch=75&memo=75&start=75](https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8/+index?batch=75&memo=75&start=75)

---


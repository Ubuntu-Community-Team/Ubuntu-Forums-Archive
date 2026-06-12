---
title: "Compiling Compiz from git source"
date: 2007-04-25
forum: Desktop Effects &amp; Customization
---

### Post by srhlefty on 2007-04-25
I'm attempting to compile compiz from source obtained through git.  I've had to go through several difficulties already, even though I have all my dependencies installed (I think :) ):

1.  Dbus.  To compile compiz you need both libdbus-1-dev and libdbus-glib-1-dev.  The installed headers ended up in /usr/include/dbus-1.0, yet when trying to compile it searches for them in /usr/include/dbus.  Not so bad, just make a link to that directory.

2.  Dbus, part 2.  Complains that dbus-arch-deps.h is missing.  After some searching, it turns out it was installed to /usr/lib/dbus-1.0/include/dbus/

3.  Mysterious linker error.  This is my question:  now I get linker errors along the lines of

```
decorator.o: In function `KWinInterface':
/home/srhlefty/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'

decorator.o: In function `Decorator':
/home/srhlefty/compiz/kde/window-decorator/decorator.cpp:245: undefined reference to `vtable for KWD::Decorator'

```

Now what am I missing?

---

### Post by srhlefty on 2007-04-25
Well I managed to find out the answer through other sources:  I just needed to reconfigure with an extra option:
```
sudo ./configure --disable-kde
```
and then do make, make install from there.

---


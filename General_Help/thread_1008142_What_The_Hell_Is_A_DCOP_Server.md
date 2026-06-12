---
title: "What The Hell Is A DCOP Server?"
date: 2008-12-11
forum: General Help
---

### Post by Mark76 on 2008-12-11
And why the hell should I care if I can't connect to it?

ChildError
: 
Errors from command '/usr/games/frozen-bubble':
Constant subroutine main::NULL redefined at /usr/games/frozen-bubble line 57
main::BEGIN() called at /usr/lib/perl5/SDL.pm line 57
eval {...} called at /usr/lib/perl5/SDL.pm line 57
Constant subroutine FBLE::NULL redefined at /usr/share/perl5/FBLE.pm line 35

ERROR: Couldn't attach to DCOP server!

ERROR: Couldn't attach to DCOP server!

Thu Dec 11 11:49:53 2008
ERROR: Couldn't attach to DCOP server!

ERROR: Couldn't attach to DCOP server!

---

### Post by eBoxNet on 2008-12-11
DCOP: Desktop COmmunications Protocol

[http://developer.kde.org/documentation/other/dcop.html](http://developer.kde.org/documentation/other/dcop.html)

---

### Post by Mark76 on 2008-12-11
Ah! So it's a KDE app?

I guess it must be used by Frozen Bubble for networked games.

---

### Post by snova on 2008-12-11
It's used to communicate between KDE programs (IPC - Interprocess Communication). There's a server that each program connects to, which relays messages appropriately.

It's been replaced with DBus in KDE 4, from what I know.

I also don't think it would affect networking...

---

### Post by Mark76 on 2008-12-14
It seems to have something to do with the zeroinstall-injector.

---


---
title: "[SOLVED] xscreensaver -exit kills X windows"
date: 2008-05-06
forum: Desktop Environments
---

### Post by mdecler2 on 2008-05-06
I am running xdm on the Ubuntu kernel 2.6.15 Dapper Drake.
When I try to exit gracefully from xscreensaver, X shuts down, and I have to login again.

I have no idea why. Anyone have any clue why?

---

### Post by mdecler2 on 2008-05-06
I answered my own question. The reason why it shut down X is because of my .xsession file was written improperly.

I had:
```
exec /usr/bin/fluxbox &
/usr/bin/xscreensaver
```

This is all wrong. So exec replaces our memory space with fluxbox, and xscreensaver is run directly on top of it. When flux dies, X will reset. I am not exactly sure why xscreensaver was killing fluxbox...

I replaced it with:
```
/usr/bin/xscreensaver &
exec /usr/bin/fluxbox
```

So now it starts xscreensaver by forking it to the background, then exec replaces the memory space with fluxbox. Now I can kill xscreensaver without killing fluxbox. When these two lines are switched around, flux doesn;t even start...

---


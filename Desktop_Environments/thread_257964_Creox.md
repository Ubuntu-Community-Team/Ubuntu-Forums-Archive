---
title: "Creox"
date: 2006-09-15
forum: Desktop Environments
---

### Post by clapton on 2006-09-15
I can't use creox, alaways I wanna run a effect appears a error without message.
Anyone knows how can I fix it?

---

### Post by hikaricore on 2006-12-20
Incase you never figured out creox, here's a simple way to start it

```
killall esd && jackd -d alsa & creox
```

This should work, but other sound on your system might not work while this is active.

You may have to:

```
killall jackd
```

To get your system sound working after closing creox.

---


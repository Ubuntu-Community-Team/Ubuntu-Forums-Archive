---
title: "Kaffeine - Doesn't play DVD's"
date: 2005-08-07
forum: Desktop Environments
---

### Post by daller on 2005-08-07
Hi there...

As far as I know, kaffeine should be able to play DVD's - right?

Starting a DVD from within kaffeine, displays this error:

Error reading NAV packet.

What could be wrong - It does it to all my DVD's (originals), and on all my computers...

Any suggestions?

---

### Post by Takis on 2005-08-07
Try installing libdvdnav4 and libdvdread3 in Kynaptic/Synaptic. They can be found in Libraries->Main.

Or

```
sudo apt-get install libdvdnav4 libdvdread3
```

---


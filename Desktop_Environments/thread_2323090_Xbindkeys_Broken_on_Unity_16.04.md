---
title: "Xbindkeys Broken on Unity 16.04??"
date: 2016-05-02
forum: Desktop Environments
---

### Post by buzzingrobot on 2016-05-02
I've used xbindkeys for a long time, but now on a fresh 16.04 Unity install it's not working. Running it in verbose mode produces this:
> 
*** Warning ***
Please verify that there is not another program running
which captures one of the keys captured by xbindkeys.
It seems that there is a conflict, and xbindkeys can't
grab all the keys defined in its configuration file.



Any guesses about that "conflict"?  (It's the tilting wheel button on a Logitech mouse.)

Does not happen on MATE 16.04 without Compiz enabled.  It does happen on MATE with Compiz enabled, with xev *not* showing the button numbers it would otherwise.

So, I vote it's Compiz.  But, is this new or is this just me finding out what's been broken all along?

---


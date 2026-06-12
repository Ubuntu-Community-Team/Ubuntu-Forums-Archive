---
title: "Media keyboard buttons configured with xmodmap are not seen by Ion3"
date: 2009-01-26
forum: General Help
---

### Post by ktvoelker on 2009-01-26
My keyboard has some media keys (play, stop, next, previous, et cetera). I have an xmodmap file which maps these keys to the proper X keysyms (XF86AudioPlay, et cetera). My window manager, Ion3, is configured to run certain commands when these keys are pressed, but it is not seeing the keypresses.

Things I have already checked:

1. When I press the keys in xev, it sees the correct keysym, so the keys must be mapped correctly.
2. xmodmap -pk also shows that the keys are mapped correctly.
3. The window manager process has the commands in its path. (It can run the commands just fine when I configure "normal" keys to run them.)

This could be an Ion bug, but the exact same configuration (for both xmodmap and Ion3) works under Debian Lenny. (I am currently on Intrepid.) So, I suspect that something Ubuntuish is catching my media keys and preventing Ion from seeing them, but I don't really know what that could be.

Any ideas?

---


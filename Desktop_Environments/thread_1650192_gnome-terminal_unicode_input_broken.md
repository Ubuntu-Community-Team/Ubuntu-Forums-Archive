---
title: "gnome-terminal: unicode input broken"
date: 2010-12-21
forum: Desktop Environments
---

### Post by lucvdv on 2010-12-21
This has been bothering me for a few different versions already, and it's still the same in 10.10: unicode character input (shift + ctrl + u hex code) is broken in gnome-terminal, it only works as long as the unicode code doesn't contain any hex digits C or F.

It's bothering me especially because my password contains a unicode character that ends in a hex C.

I once found a workaround that fixed the problem in 9.04 (or even longer ago), but now I just installed a new copy of 10.10 and I can't seem to find that workaround anymore.

It probably comes down to disabling the normal shortcuts (copy and find), but only for terminal, because copy still worked in other apps on that previous setup.

Can anyone help me remember?


It would be even better if this could be fixed in a next release of gnome-terminal.  That probably would mean to temporarily disable ctrl+shift+C and ctrl+shift+F as soon as ctrl+shift+U is pressed and until ctrl and shift have been released.

---


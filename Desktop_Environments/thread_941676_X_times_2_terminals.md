---
title: "X times 2 terminals"
date: 2008-10-08
forum: Desktop Environments
---

### Post by Armor Nick on 2008-10-08
Hey everyone,

first of all, I didn't know where to put this so if this is the wrong forum, excuse me ;) .

second of all, sorry about the strange title but it will become clear soon.

Theoretically, linux has got seven virtual terminals, with one running the X system. Also theoretically, X is a program, just like KDE, gedit, lynx and ls. So, theoretically, it would be possible to start X on more than one virtual terminal. However, I currently don't have access to Linux, so I can't try it. Not that I was going to, since I'm not a Linux expert yet :D .

Any feedback? Anyone tried this? Anyone going to try this?

**Note:** newbies beware, there is a big chance that this will freeze your computer and/or mess up X. Then again, I might be wrong ;)

---

### Post by maybeway36 on 2008-10-08
On a stock Ubuntu install, what I would do is press Ctrl+Alt+F1 and log in, then type:
```
startx -- :1
```
I use :1 because :0 is taken (it' the automatic one.) The new X session should be on either F8 or F9, and you can switch back and forth.

---


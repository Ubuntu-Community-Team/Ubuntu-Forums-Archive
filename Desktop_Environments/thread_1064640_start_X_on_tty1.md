---
title: "start X on tty1"
date: 2009-02-09
forum: Desktop Environments
---

### Post by jackm on 2009-02-09
Hi all,
I switch on console tty1, and I tried to start X I get : 
```
Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.

```
how to resolve that :?:

---

### Post by kerry_s on 2009-02-09
type startx -- :1
type startx -- :2 
type startx -- :3
and so on for as many as your vid card/memory can stand.

---

### Post by jackm on 2009-02-09
thanx **kerry_s** it works :)
but when I leave **tty1** and come back I get the following error and **X** stops working :
```
The XKEYBOARD keymap complier (xkbcomp) reports :
Warning   Type "ONE_LEVEL" has one levels, but <RALT> has tow symbols
         Ignoring extrat symbols
Errors from xkbcomp are not fatal to the X server
```
any ideas :?:

---

### Post by kerry_s on 2009-02-09
> **jackm said:**
> thanx **kerry_s** it works :)
but when I leave **tty1** and come back I get the following error and **X** stops working :
```
The XKEYBOARD keymap complier (xkbcomp) reports :
Warning   Type "ONE_LEVEL" has one levels, but <RALT> has tow symbols
         Ignoring extrat symbols
Errors from xkbcomp are not fatal to the X server
```
any ideas :?:

nope, have no ideas, never really played with it.
are you using a different user? i think that would be best.
just being curious, why do you need more than 1 xsession?

---


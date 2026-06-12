---
title: "Messed up man pages"
date: 2006-09-08
forum: Desktop Environments
---

### Post by PathSpace on 2006-09-08
My man pages are really messed up; they contain all sorts of strange symbols, such as squares and stuff.  Some man pages, such as the one for aptitude, are pretty much unreadable due to all the bizarre characters cluttered all over the place.  Anyone know how I might could fix this?

---

### Post by TylerRick on 2008-05-13
Yeah, I've gotten that too sometimes...

See [http://ubuntuforums.org/showthread.php?t=389671](http://ubuntuforums.org/showthread.php?t=389671)

> **Mr. C. said:**
> Is this in Terminal , or a teminal emulator such as putty, securecrt, or ...?

You're seeing the output of bold or overstrike formatting, and your terminal type does not match the set terminal type.

```
echo $TERM
```

and see if this matches your terminal type.  If not, change either the emulator, or the TERM environment variable, as in:

```
TERM=vt100
TERM=xterm
TERM=linux
```

as appropriate.

MrC

---


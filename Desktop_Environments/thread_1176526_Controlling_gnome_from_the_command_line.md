---
title: "Controlling gnome from the command line"
date: 2009-06-02
forum: Desktop Environments
---

### Post by mofrikaantje on 2009-06-02
Hi,
I'm looking for a way to control gnome from the command line (terminal): things like going to the next windows, desktop 2, maximize window, etc. I already looked on the interwebs and searched the forums, but no result. Is there a way to do this?

---

### Post by zhocchao on 2009-06-02
wmctrl can be helpful

---

### Post by uupreti on 2009-06-02
Yeah **wmctrl **is something that can interact with X-manager from command line.

---

### Post by mofrikaantje on 2009-06-03
True, wmctrl has some options, but not just switching to the next window, or maximising it, etc. Aren't there any other extensions available that could do the trick, or - simply - are there command line options available to control gnome *directly*?
Sorry for bugging you guys with it, I'm just trying to get some voice control program to do the things I want, like switching to another window :)

Cheers

---

### Post by zhocchao on 2009-06-03
Don't know about command line options. But you could simulate the key for the action
e.g.
xte 'keydown Alt_L' ;xte 'key F2' ;xte 'keyup Alt_L'
or
xte 'keydown Alt_L' ;xte 'key Tab' ;xte 'keyup Alt_L'

---

### Post by mofrikaantje on 2009-06-03
> **zhocchao said:**
> Don't know about command line options. But you could simulate the key for the action
e.g.
xte 'keydown Alt_L' ;xte 'key F2' ;xte 'keyup Alt_L'
or
xte 'keydown Alt_L' ;xte 'key Tab' ;xte 'keyup Alt_L'

This pretty much looks like what I was looking for. I've tested some commands, including Page Down, and it works! Thanks :D Yelling "next window" at my computer works now!

---

### Post by zhocchao on 2009-06-04
does it really work? (alt+tab). I tried it with strokes, but when i have 4 windows open, 1 is never activated.

---


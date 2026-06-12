---
title: "cheating tool"
date: 2007-10-04
forum: Gaming &amp; Leisure
---

### Post by joetexeira on 2007-10-04
Hey everyone.  Does anyone know of a game cheating tool for ubuntu?   Something that I can use to scan the memory of a running game, find a certain value, and change that value to something else?

Thanks:popcorn:

---

### Post by justin whitaker on 2007-10-04
Most of the folks around here look down on that sort of thing. 

Just saying.

---

### Post by PrimoTurbo on 2007-10-04
> **justin whitaker said:**
> Most of the folks around here look down on that sort of thing. 

Just saying.

He wants a memory scanner which doesn't work in 99% of multiplayer games. I am guessing he wants it for personal use on a single player game, why would anyone look down on that exactly?...

I don't know about any memory scanners for Linux but Windows has tons.

---

### Post by joetexeira on 2007-10-07
> **PrimoTurbo said:**
> He wants a memory scanner which doesn't work in 99% of multiplayer games. I am guessing he wants it for personal use on a single player game, why would anyone look down on that exactly?...

I don't know about any memory scanners for Linux but Windows has tons.


That's pretty much exactly what I want it for.   
Anyone know of one?   Do they not exist on Linux??
:confused:

---

### Post by Cannaregio on 2007-10-07
I wonder if you could use valgrind.
It's a memory debugger (in fact a profiler), but it tracks all read/writes to memory.

---

### Post by Everywhere_at_Once on 2007-10-07
if anyone here DOESNT look down on cheating, then you *shouldnt be allowed to game.*
Cheating is just for people who are too lazy to actually get good, so they need a crutch. bug pu**ys. 
Cheating is the single most frustrating thing about online gaming, so yeah, I look down on it.

---

### Post by radzh on 2007-10-07
QGSpider is the tool of choice.

---

### Post by cogadh on 2007-10-07
> **Everywhere_at_Once said:**
> if anyone here DOESNT look down on cheating, then you *shouldnt be allowed to game.*
Cheating is just for people who are too lazy to actually get good, so they need a crutch. bug pu**ys. 
Cheating is the single most frustrating thing about online gaming, so yeah, I look down on it.
Well, that was awfully close-minded of you. Cheating in multi player games should definitely be discouraged, but what is the problem with using cheats in a single player game? It's a matter of personal choice and none of your concern. It doesn't make you less of a gamer to use some cheats (i.e. "add item" cheats and the like), it just means you have a different style of play. Besides, after you have played through a game a half dozen times or so, cheating is pretty much the only way to get anything new out of a game (other than mods).

@joetexeira: As for an app that might help, I think GDB might do what you need:
[http://www.gnu.org/software/gdb/gdb.html](http://www.gnu.org/software/gdb/gdb.html)

---

### Post by joetexeira on 2007-10-10
> **cogadh said:**
> ...Besides, after you have played through a game a half dozen times or so, cheating is pretty much the only way to get anything new out of a game (other than mods)...


That's exactly why I'm looking for such a program..!:KS

I checked out GDB, but I'm not sure that it does what I would want.

@radzh, you pointed out QGSpider which looks like it's the right tool, however it doesn't compile well (or really at all).   I've gotten an assortment of errors from it while trying to compile.   I don't suppose there's a deb for it somewhere?

Or is there a better tool out there?
:popcorn:

---

### Post by radzh on 2007-10-10
> **joetexeira said:**
> @radzh, you pointed out QGSpider which looks like it's the right tool, however it doesn't compile well (or really at all).   I've gotten an assortment of errors from it while trying to compile.   I don't suppose there's a deb for it somewhere?:popcorn:
You were compiling patched sources, right? Nevermind, here is binary attached. Hope it'll suffice; i've got only binary file on my home machine. Just put it into your usr/local/bin

Only other tool comes to mind is KCheat, tho i can't tell if it's good.

---

### Post by joetexeira on 2007-10-26
Hey radzh,

   I tried out your binary but it was a no-go.   Could you point me to the patched source you used to compile your QGSpider, or some instructions on how to get it running on gutsy?   Or if someone knows of a deb for it, that might be better...   Thanks!!
:popcorn:

---

### Post by radzh on 2007-12-15
> **joetexeira said:**
> Hey radzh,

   I tried out your binary but it was a no-go.   Could you point me to the patched source you used to compile your QGSpider, or some instructions on how to get it running on gutsy?   Or if someone knows of a deb for it, that might be better...   Thanks!!
:popcorn:

Sorry for late answer, i never got a notification.
I can't help you with old sources, as i just got them, applied the patch attached, then compiled everything ok. Never touched that thing again.

But.
Here it is: [http://sourceforge.net/projects/qgspider](http://sourceforge.net/projects/qgspider)
Here is some discussion: [http://www.happypenguin.org/show?QGSpider](http://www.happypenguin.org/show?QGSpider)

The 2.0 version. Maybe i will compile it for my brand new 64-bit Gutsy now :)

Hope it helps.

---

### Post by radzh on 2007-12-15
Tough luck, there is no way for 64-bit compilation. I'll try it on my 32-bit laptop soon.

Am going to contact author. Maybe he'll need some help.

---


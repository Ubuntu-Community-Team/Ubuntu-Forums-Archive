---
title: "libSDL for amd64 ?"
date: 2006-06-09
forum: Gaming &amp; Leisure
---

### Post by Sandsound on 2006-06-09
Hi all

Im trying to run a rather cool game (Saurbraten) on my amd64 instlation, but I keep getting an error :

"error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory"

In my Synaptic package maneger I can only see a libsdl-1.2.9... ? wich I already have installed.

Do I have to downgrade my libsdl to play this game ? and if so... how do I do that ?


btw... Saurbraten ( [http://sauerbraten.org/](http://sauerbraten.org/) ) is a 3d FPS. I have seen it in action on my husbands pc (i386) and it works fine there, actualy I cant understand why this game isnt in my package maneger ? its SO cool :-)

---

### Post by wmcbrine on 2006-06-09
A dependency for libSDL-1.2 should be satisfied by 1.2.9 -- you can think of the 1.2 as "1.2.x".

My guess is that you're trying to run a 32-bit binary, and you don't have the 32-bit version of libSDL installed.

---

### Post by Sandsound on 2006-06-09
[QUOTE=wmcbrine]My guess is that you're trying to run a 32-bit binary, and you don't have the 32-bit version of libSDL installed.[/QUOTE]

Yes... its a 32-bit ( cant find a prober 64-bit game ).

Cant I somehow install the 32-bit sdl ? without destroying my exelent 64-bit system ofcourse :-)

---

### Post by wmcbrine on 2006-06-09
Yes. You're probably going to have to set up a chroot. Check out the 64-bit Users forum for more on that.

---

### Post by Sandsound on 2006-06-09
[QUOTE=wmcbrine]Yes. You're probably going to have to set up a chroot. Check out the 64-bit Users forum for more on that.[/QUOTE]

Ok... Ill do that, but I dont have the slightest idea of what a "chroot" is :-)

---


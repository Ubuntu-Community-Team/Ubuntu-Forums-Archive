---
title: "&quot;No available video device&quot; error with SDL"
date: 2007-08-20
forum: Desktop Environments
---

### Post by hailtothethief on 2007-08-20
Running Edgy on a 56k modem, making update impractical.

While trying to install freedroidRPG I also installed one of its dependencies, SDL, along with some associated packages (SDL_images and SDL_net). After (apparently) successfully installing these packages I compile freedroidRPG using 

```
./configure
make
sudo make install
```

Standard procedure, no switches. I then moved to execute the application, and I received the following embedded in some cute ASCII dividers:

```
Hello, this is FreedroidRPG, version 0.10.3rc2.
This seems to be a 'stable' release, so no exit on floating point exceptions.
-Signal Handling------------------------------------------------------
Setting up signal handlers for internal backtrace:
Now catching SIGSEGV: YES
Now catching FPE (if raised, that is!): YES

Couldn't initialize SDL: No available video device

----------------------------------------------------------------------
Termination of freedroidRPG initiated...Thank you for playing freedroidRPG.
```

Tragic.

When executing another SDL dependent app (zsnes) I get approximately the same thing:

```
Could not set 512x448video mode: no video device available.
```

I couldn't find any SDL packages on the Ubuntu packages server, save for plug-ins for unrelated programs. Am I making some sort of ubern33b mistake? Are SDL and Ubuntu fundamentally incompatible? Am I doomed to spend the next week downloading Feisty? Someone please help me.

---

### Post by cdaringe on 2008-03-05
did you ever solve this?

---

### Post by Pierre Monteux on 2008-03-20
I just encountered this same issue, found the solution here.
[http://listas.apesol.org/pipermail/sdl-libsdl.org/2001-October/020902.html](http://listas.apesol.org/pipermail/sdl-libsdl.org/2001-October/020902.html)

long story short, if the develepment libraries for the xserver are not installed sdl compiles without x11 support, so no video device.

running "aptitude install gnome-devel" then reconfinguring and compiling sdl fixed it for me.

---


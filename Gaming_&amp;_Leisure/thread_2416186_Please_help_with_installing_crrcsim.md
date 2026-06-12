---
title: "Please help with installing crrcsim"
date: 2019-04-06
forum: Gaming &amp; Leisure
---

### Post by rva1945 on 2019-04-06
Hi, I downloaded the package from here

[https://sourceforge.net/projects/crrcsim/](https://sourceforge.net/projects/crrcsim/)

but then ./configure gives this after some lines:
...
* The sdl-config script installed by SDL could not be found * If SDL was installed in PREFIX, make sure PREFIX/bin is in * your path, or set the SDL_CONFIG environment variable to the * full path to sdl-config. configure: * SDL version 1.2.5 or newer not found! See if at least 1.2.0 is present... checking for sdl-config... (cached) no checking for SDL - version >= 1.2.0... no * The sdl-config script installed by SDL could not be found * If SDL was installed in PREFIX, make sure PREFIX/bin is in * your path, or set the SDL_CONFIG environment variable to the * full path to sdl-config. configure: error: * SDL version 1.2.0 or newer not found!&#65279;

I'd appreciate any help!

---

### Post by #&amp;thj^% on 2019-04-06
just a guess but:
```
sudo apt-get install libsdl1.2-dev libsdl-image1.2-dev
```
It may ask for or need guile also.
```
sudo apt-get install guile-1.8-dev

```
Then run ./configure again.
Good Luck

---


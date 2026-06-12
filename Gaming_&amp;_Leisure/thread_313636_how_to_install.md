---
title: "how to install"
date: 2006-12-06
forum: Gaming &amp; Leisure
---

### Post by aco on 2006-12-06
Ok i downloaded openmortal-0.7.tar.bz2....now how to install it

---

### Post by haxer on 2006-12-06
cd to its "location" then ./configure make then sudo make install? :-k I never got it to work

---

### Post by Perfect Storm on 2006-12-06
> **aco said:**
> Ok i downloaded openmortal-0.7.tar.bz2....now how to install it

Extract the tarball, then cd into it and ls -a, please post it.

---

### Post by lesbianpenguin on 2008-11-13
hi... im having problem to ./configure in the folder...

i may not having any dependencies... currently it stuck at

checking for SDL - version >= 1.2.0... yes
checking for IMG_Load in -lSDL_image... no
configure: error: *** SDL_image library not found!

in readme it stated it need SDL-devel, SDL_image-devel, SDL_mixer-devel, freetype2-devel and perl-devel...

any idea how to install those dependencies

---

### Post by Perfect Storm on 2008-11-13
> **lesbianpenguin said:**
> hi... im having problem to ./configure in the folder...

i may not having any dependencies... currently it stuck at

checking for SDL - version >= 1.2.0... yes
checking for IMG_Load in -lSDL_image... no
configure: error: *** SDL_image library not found!

in readme it stated it need SDL-devel, SDL_image-devel, SDL_mixer-devel, freetype2-devel and perl-devel...

any idea how to install those dependencies

Check Synaptic Package Manager for those files.

By the way please don't resurrect 2 years old threads. Make a new one instead next time.

---

### Post by lesbianpenguin on 2008-11-13
hey... manage to install some dependencies.... however solve this error

configure: error: *** SDL_net library not found!

---

### Post by Grishka on 2008-11-13
> **lesbianpenguin said:**
> hey... manage to install some dependencies.... however solve this error

configure: error: *** SDL_net library not found!

[apt://libsdl-net1.2-dev]("apt://libsdl-net1.2-dev")

---


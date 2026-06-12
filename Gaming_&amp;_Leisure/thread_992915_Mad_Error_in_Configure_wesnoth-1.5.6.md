---
title: "Mad Error in Configure wesnoth-1.5.6"
date: 2008-11-25
forum: Gaming &amp; Leisure
---

### Post by Vahids on 2008-11-25
i Download source code of wesnoth-1.5.6 , i think it's a good game BUT,
i have error to configyre!!!:
> 
.
.
.
checking Python.h usability... yes
checking Python.h presence... yes
checking for Python.h... yes
checking for Py_Finalize in -lpython2.5... yes
checking for libpng-config... /usr/bin/libpng-config
[B]checking for SDL - version >= 1.2.7 and SDL_ttf - version >= 2.0.8... no
configure: error: *** Please upgrade your SDL version
[/B]

:(
my sdl version:
> vahid@vahid-desktop:~/build$ sdl-config --version
1.2.13

and not 1.2.7 !
My sdl ttf and dev Version is:
> 2.0.9

Help me please!:confused:

---

### Post by eragon100 on 2008-11-25
I have the same problem, does anyone know what to do about this??

---

### Post by Perfect Storm on 2008-11-25
Notify the wesnoth devs about it, there might be a bug in configure files.

1.5.5 works without issue though.

---

### Post by Vahids on 2008-11-25
> **Artificial Intelligence said:**
> Notify the wesnoth devs about it, there might be a bug in configure files.

1.5.5 works without issue though.
not any else way? 
my internet is very slow and expensive, it's hard for me to download 130 MB again!
Please,

---

### Post by happyhamster on 2008-11-25
Try compiling after:

sudo apt-get build-dep wesnoth

sudo apt-get install libsdl-ttf2.0-dev

Good luck.

---

### Post by eragon100 on 2008-11-26
> **happyhamster said:**
> Try compiling after:

sudo apt-get build-dep wesnoth

sudo apt-get install libsdl-ttf2.0-dev

Good luck.

Well, I had already done sudo apt-get build-dep wesnoth, but that only installs the dependencies needed for the version of wesnoth in intrepid´s official repos, which is 1.4.5. Because there are a lot of fundamental changes in the 5.x series, such as the new editor for example, the dependencies have changed as well. I haven´t tried the other command yet, I will see if it helps when I come home. Thanx for the suggestion!

EDIT: It configures and is now building! Thanx a lot!

sudo apt-get build-dep wesnoth

and then

sudo apt-get install libsdl-ttf2.0-dev

solves the problem :) Have fun everyone!

---

### Post by Perfect Storm on 2008-11-26
You could just checked here; [http://gaming.gwos.org/doku.php/guides:64bit:battle_for_wesnoth](http://gaming.gwos.org/doku.php/guides:64bit:battle_for_wesnoth) to get it right first time ;)

---


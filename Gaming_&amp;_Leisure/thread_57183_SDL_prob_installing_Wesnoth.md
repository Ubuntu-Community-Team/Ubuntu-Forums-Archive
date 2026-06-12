---
title: "SDL prob installing Wesnoth"
date: 2005-08-15
forum: Gaming &amp; Leisure
---

### Post by shawn on 2005-08-15
I have been trying to install Wesnoth but i get this when I ./configure :

configure: error: *** SDL not found! Get SDL from [www.libsdl.org](www.libsdl.org).

I did an apt-cache search for SDL but I dont know which things to intall. Any help would be appreciated!

---

### Post by jdodson on 2005-08-15
[QUOTE=shawn]I have been trying to install Wesnoth but i get this when I ./configure :

configure: error: *** SDL not found! Get SDL from [www.libsdl.org](www.libsdl.org).

I did an apt-cache search for SDL but I dont know which things to intall. Any help would be appreciated![/QUOTE]

right.

install the sdl dev* packages.  that should help.

i think it needs:

sdl mixer dev
sdl net dev
sdl png dev (maybe images)

.....
i think the readme says what you need specifically.

---

### Post by shawn on 2005-08-15
Got it, thanks!

---

### Post by mufftin on 2005-09-07
@jdodson: Thank you. that helped!

Sincerely, Mufftin

---


---
title: "Warzone 2100 - SDL_net not found"
date: 2006-07-08
forum: Gaming &amp; Leisure
---

### Post by chadk on 2006-07-08
When I ./configure I get:
checking for SDL - version >= 1.1.4... yes
checking for presence of SDL_net... Could not find SDL_net
configure: error: SDL_net is not installed

When I try apt-get ...
libsdl-net1.2 is already the newest version.


?
Is there another SDL_net?

---

### Post by chadk on 2006-07-08
Usually there's a reply pretty quick.  Anyone know about this SDL_net ?

---

### Post by Ptero-4 on 2006-07-09
Install sdl_net-dev, that package contain the headers and includes needed for compiling apps from source.

---

### Post by CameronCalver on 2007-01-05
Chadk did you ever get that to work becuase im trying now and i get the same error

---

### Post by Bastanteroma on 2007-01-09
I installed the libsdl-net1.2-dev package and then things worked (although the game doesn't display in full-screen).

Don't know if that package was in an official repo or one that Automatix enabled.

---


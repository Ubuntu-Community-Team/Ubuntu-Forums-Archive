---
title: "configure: error: *** SDL version 1.1.3 not found!"
date: 2006-06-15
forum: Desktop Environments
---

### Post by ph33r213 on 2006-06-15
Hey, I was trying to configure gnome-gens, and well, I got this error

checking target system type... /bin/sh: ./config.sub: No such file or directory

checking for sdl-config... no
checking for SDL - version >= 1.1.3... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: *** SDL version 1.1.3 not found!

I looked in packages.ubuntu.com, and Synaptic, but I couldn't find that one version, and Synaptic said I already had it. Whats wrong?

---

### Post by FredB on 2006-06-15
Did you install development packages, "-dev" ones ?

---

### Post by ph33r213 on 2006-06-15
Sorry, but I don't get what you mean. :( I looked on [this page]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=sdl&searchon=names&subword=1&version=dapper&release=all") but couldn't find anything like, sdl-dev or something like that.

---

### Post by FredB on 2006-06-15
This one, maybe : libsdl1.2-dev

---

### Post by ph33r213 on 2006-06-15
Ok, I'm trying to get that one, but, theres so many dependencies. :( Is there any way I can download them all at once? I tried apt-get-ing it, and it said it couldn't find it, same with Synaptic.

---


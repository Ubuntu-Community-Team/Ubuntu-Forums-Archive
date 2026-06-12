---
title: "Compiling Battle for Wesnoth, SDL not found"
date: 2007-03-24
forum: Gaming &amp; Leisure
---

### Post by MiCovran on 2007-03-24
I installed Battle for Wesnoth with Synaptic and played it with no problems, until i tried to play in multiplayer. It says that i have a version 1.1.8 and that i need 1.1.12 or later.

I went to [www.wesnoth.org](www.wesnoth.org) and found a new version in source code. I never compiled any source code before, but I haven't found any other way. I uninstalled the old version and followed all the steps [here]("http://www.wesnoth.org/wiki/CompilingWesnoth") and extracted everything to '/usr/share/games/wesnoth-1.2.3'. Now, when I get to the './configure' part, i get this message (after a big list):
```
(...)
checking for X... no
checking for XOpenDisplay in -lX11... no
checking for sdl-config... no
checking for sdl11-config... no
configure: error: *** SDL not found! Get SDL from www.libsdl.org.
If you already installed it, check it's in the path. If problem remains,
please send a mail to the address that appears in ./configure --version
indicating your platform, the version of configure script and the problem.
```

I just don't get it. I have installed all the packages mentioned before. What is the problem?

Thanks.

---

### Post by invalid on 2007-03-24
Try```
sudo apt-get install libsdl-dev
```

---

### Post by MiCovran on 2007-03-24
Thank you for a quick response. It worked. I installed all the '-dev' packages and finished all the steps from [http://www.wesnoth.org/wiki/CompilingWesnoth](http://www.wesnoth.org/wiki/CompilingWesnoth).

Please, could someone tell me how to run a game after the 'sudo make install'?

---

### Post by Perfect Storm on 2007-03-24
type wesnoth in the terminal

---

### Post by MiCovran on 2007-03-24
```
bash: wesnoth: command not found
```
I tried that already. :)

---

### Post by Perfect Storm on 2007-03-24
Then it's properly not installed. Try check back and see if any error output was shown.

---

### Post by MiCovran on 2007-03-24
Unbelievable! I just repeated './configure', 'make' and 'make install' and now it works. Maybe i missed a sudo or something...

Anyway, thanks a lot for help.

---


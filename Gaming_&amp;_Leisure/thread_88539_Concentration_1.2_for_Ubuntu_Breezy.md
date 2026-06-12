---
title: "Concentration 1.2 for Ubuntu Breezy"
date: 2005-11-10
forum: Gaming &amp; Leisure
---

### Post by Tomasz on 2005-11-10
Hi, I've made a .deb package of Concentration 1.2 for Ubuntu Breezy. Concentration is a classic memory game and it's fun to play even for grown-ups (spin those rusty cogs ;) ). The official .deb is outdated and I'm not even sure that it is suitable for Breezy.

[Download](http://tomasz.nukysrealm.net/concentration_1.2-1_i386.deb) the file to your home folder and install it by typing this in the terminal:

```

sudo dpkg -i concentration*.deb

```

You might not have all the dependencies, so sort them out this way:
```

sudo apt-get -f install

```
If you still have problems with dependencies then you need the following packages: SDL 1.2.x, SDL_mixer 1.2.x,SDL_image 1.2.x and SDL_ttf 2.x.

It works fine here(TM). To run it, just type:
```
concentration
``` and hit enter.

---


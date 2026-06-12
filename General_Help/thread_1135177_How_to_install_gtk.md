---
title: "How to install gtk?????????"
date: 2009-04-24
forum: General Help
---

### Post by mubbashar on 2009-04-24
please tell how to install gtk .

---

### Post by Judgegeo on 2009-04-24
You can use

```
sudo aptitude install ubuntu-desktop
```

---

### Post by Chris_82 on 2010-05-13
Ok it's true that this thread is old but I wanted too add my discoveries somewhere useful..so maybe this is the place.
Did you want to install the gtk+ packages to build your own GUI applications? If yes then the following will let you do this:
```

sudo apt-get install build-essentials libgtk2.0-dev libgtk2.0-doc devhelp

```
The last one **devhelp** is useful if you want to have a nice off-line documentation. Devhelp will be available in Applications/Programming/.

Now some people install the meta-package **gnome-core-devel** too..on my system this one would add over 100 additional packages. I didn't do it yet but might have to do it later..

A simple c source file is compiled with this command:
```
gcc -o simple simple.c $(pkg-config --libs --cflags gtk+-2.0)
```

cheers

---


---
title: "Descent 1 or 2  anyone?"
date: 2007-10-11
forum: Gaming &amp; Leisure
---

### Post by Mochtroid-X on 2007-10-11
Has anyone managed to get D2X, D2X-XL, or DXX-Rebirth to successfully install? All of them will finish ./configure properly but none of them will finish make or scons without errors! Is this even possible to install these or should I break out a Windows disc and get to partitioning? I've tried going to their forums only to find no help whatsoever, an administrator even locking my post after repeating exactly what I said. Their install instructions are horrible.  Can anyone help me?

---

### Post by macabro22 on 2007-10-27
hmm.. I would like to install that as well

---

### Post by DoktorSeven on 2007-10-28
What errors do make/scons give you when you compile?

Edit: d2x-rebirth seemed to compile fine here (on Gutsy) when the -dev packages needed to compile were installed (it seems to need at least SDL and libphysfs, maybe more -- look at the error messages and see if it says that it can't find a certain header or library to determine which -dev packages you might need).

---

### Post by glennric on 2009-12-13
I don't know if you figured this out or not, or are still interested, but I created packages for d2x-xl.  They are in my ppa.  Add the lines
```

deb http://ppa.launchpad.net/glennric/d2x-xl/ubuntu karmic main
deb-src http://ppa.launchpad.net/glennric/d2x-xl/ubuntu karmic main

```
to your /etc/apt/sources.list file.
Then install the package "d2x-xl".  You then can install the "d2x-xl-demo" package or copy the required Descent 2 data files to /usr/share/games/d2x-xl/data.
If you run the game from a terminal without the demo or the needed game files it will tell you what files are needed.  Make sure the filenames are all lower case.

---

### Post by Sand &amp; Mercury on 2009-12-14
> **glennric said:**
> I don't know if you figured this out or not, or are still interested, but I created packages for d2x-xl.  They are in my ppa.  Add the lines
```

deb http://ppa.launchpad.net/glennric/d2x-xl/ubuntu karmic main
deb-src http://ppa.launchpad.net/glennric/d2x-xl/ubuntu karmic main

```
to your /etc/apt/sources.list file.
Then install the package "d2x-xl".  You then can install the "d2x-xl-demo" package or copy the required Descent 2 data files to /usr/share/games/d2x-xl/data.
If you run the game from a terminal without the demo or the needed game files it will tell you what files are needed.  Make sure the filenames are all lower case.
You legend. :D Though I'm no longer running Linux, I think everyone who hasn't before should take Descent 2 for a spin. Awesome game.

---

### Post by thomaszmark on 2009-12-14
Descent 1 is a good game, any interesting, plz give me

---

### Post by handy on 2009-12-15
Descent 1, 2, 3 & Freespace all have silver ratings for Crossover. So they probably work ok on Wine.

---


---
title: "Problem with shared libraries when starting Wesnoth"
date: 2008-10-13
forum: Gaming &amp; Leisure
---

### Post by beleth on 2008-10-13
I went to go play some delicious wargame with a friend of mine, only to find the following error message when I tried to start the game from terminal:

```
$ wesnoth
wesnoth: error while loading shared libraries: libboost_iostreams-gcc-mt-1_33_1.so.1.33.1: cannot open shared object file: No such file or directory

```

Used aptitude to purge and reinstall (which I didn't really expect to solve the problem,) and it's still throwing me the same error message. Tried to use synaptic to grab the libraries it says it doesn't have, but they were already installed and reinstalling didn't help.

Any ideas?

---

### Post by Perfect Storm on 2008-10-14
This package of Wesnoth - is it one that comes default with Ubuntu or did you get it from your friend or a 3rd party repo?

---


---
title: "Free game for Linux involving physics"
date: 2008-02-20
forum: Gaming &amp; Leisure
---

### Post by Sockerdrickan on 2008-02-20
[http://www.acc.umu.se/~emilk/index.html](http://www.acc.umu.se/~emilk/index.html) :popcorn: Have fun guys

[http://www.youtube.com/watch?v=0H5g9VS0ENM](http://www.youtube.com/watch?v=0H5g9VS0ENM)

---

### Post by madsmeg on 2008-02-20
Darn "Education" block, yeah thats right, my work blocks EVERYTHING! cant even access Uni, thank the lord for Ubuntu forums :D

---

### Post by FrozenFox on 2008-02-20
Lol, entertaining. I set up a little scene with a stick figure dood and a basketball court and threw the ball circle in. OH, INTO THE STANDS!

Ty

---

### Post by grossaffe on 2008-02-20
i can see myself wasting a lot of time with that... kinda like when i first installed ubuntu and was messing with the Compiz stuff.

edit:  little help guys?  can't seem to get it running:
```
./phun: error while loading shared libraries: libaudio.so.2: cannot open shared object file: No such file or directory
```

---

### Post by Sockerdrickan on 2008-02-21
sudo apt-get install libaudio2

---

### Post by hungryOrb on 2008-02-21
OH looks awesoems! Like crayon physics? That was so cool gem! Its those physics games (like the old and early ACROSS) that captivate so much imagination!

---

### Post by grossaffe on 2008-02-21
> **Tux0r said:**
> sudo apt-get install libaudio2

that did the trick, thanks.

---

### Post by matthewcraig on 2008-02-22
> **Vadi said:**
> I had that problem too, but I got the libglew-1.5 package from synaptic, and it worked.

You'll get the error *error while loading shared libraries: libGLEW.so.1.5* when trying to run this program with Gutsy.

Ubuntu Gutsy comes with v 1.4 of GLEW, but you don't need to override this library!!  The Phun download comes with the correct version.

Just run the program with this command line:

```
LD_LIBRARY_PATH=. ./phun
```

FYI, 08.04 will have v 1.5

---

### Post by CharlesA on 2011-10-21
Back to sleep...

---


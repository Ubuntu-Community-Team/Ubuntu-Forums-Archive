---
title: "L-Echo - echochrome clone"
date: 2008-05-10
forum: Gaming &amp; Leisure
---

### Post by JT673 on 2008-05-10
New L-Echo Version (0.2.8 ):

[http://www.youtube.com/watch?v=IneVCkBZCrc](http://www.youtube.com/watch?v=IneVCkBZCrc)

Old N-Echo (0.2.3) (fuzzy video is fuzzy):

[http://www.youtube.com/watch?v=27OCqz1gTLM](http://www.youtube.com/watch?v=27OCqz1gTLM)

During the summer I only had enough time to strengthen the code and add proper stairs (and spheres to nds version), but things should go back on track now.

Same place:

[http://code.google.com/p/l-echo/](http://code.google.com/p/l-echo/)

---

### Post by JT673 on 2008-05-11
Bump

---

### Post by dudeofthedead on 2008-05-11
```
Segmentation fault
```

---

### Post by JT673 on 2008-05-11
Uhoh, really?  Try compiling this new version:

[http://www.mediafire.com/?nm4cfp3lymw](http://www.mediafire.com/?nm4cfp3lymw)

---

### Post by dudeofthedead on 2008-05-11
```
%@%:~/Desktop/l-echo/src$ ls -la
total 64
drwxr-xr-x 2 hzf hzf 4096 2008-05-12 00:11 .
drwxr-xr-x 3 hzf hzf 4096 2008-05-10 00:47 ..
-rw-r--r-- 1 hzf hzf 1994 2008-05-12 00:01 echo_gfx.cpp
-rw-r--r-- 1 hzf hzf  938 2008-05-11 23:50 echo_gfx.h
-rw-r--r-- 1 hzf hzf 2019 2008-05-12 00:11 echo_math.cpp
-rw-r--r-- 1 hzf hzf 1460 2008-05-11 23:59 echo_math.h
-rw-r--r-- 1 hzf hzf 2475 2008-05-11 21:13 echo_ns.cpp
-rw-r--r-- 1 hzf hzf  979 2008-05-11 21:42 echo_ns.h
-rw-r--r-- 1 hzf hzf 3248 2008-05-12 00:10 escgrid.cpp
-rw-r--r-- 1 hzf hzf 1900 2008-05-11 21:35 escgrid.h
-rw-r--r-- 1 hzf hzf 3664 2008-05-11 23:47 grid.cpp
-rw-r--r-- 1 hzf hzf 1850 2008-05-11 21:18 grid.h
-rw-r--r-- 1 hzf hzf 5238 2008-05-12 00:06 main.cpp
-rw-r--r-- 1 hzf hzf  141 2008-05-11 20:02 Makefile
-rw-r--r-- 1 hzf hzf  845 2008-05-11 02:40 scite.ssn
```

No configure file or l-echo...

---

### Post by JT673 on 2008-05-11
Sorry, you'll have to compile it.

```
sudo apt-get install build-essentials libgl1-mesa-dev libfreeglut3-dev
make
```

When did the old version seg fault, by the way?  Like, right when you started it, or during the demo?

---

### Post by dudeofthedead on 2008-05-11
Okay, I didn't realize there was a Makefile inside the src directory!

I have every possible glut library installed but when I 'make', I get

```
gcc *.o -lGL -lGLU -lglut -lpthread -o l-echo
```

The old version would seg fault on me right from the start when I './l-echo'.

---

### Post by dudeofthedead on 2008-05-11
It's working now!

[http://www.mediafire.com/?10wen1gbzyz](http://www.mediafire.com/?10wen1gbzyz)

Seems there's no need to worry about the previous output.

---

### Post by JT673 on 2008-05-11
You know, this is really strange...The exe is giving me a page fault, but the ELF isn't...

Anyway new version (the version dudeofthedead downloaded).

---

### Post by JT673 on 2008-05-17
Bump

---

### Post by dudeofthedead on 2008-05-18
The game won't let me choose a new riddle when I finish the first one.

---

### Post by JT673 on 2008-05-20
more bumpage

---

### Post by dudeofthedead on 2008-05-20
Why don't you answer the question first...

---

### Post by JT673 on 2008-05-24
Mega update bumpzorz

---

### Post by JT673 on 2008-05-24
Oh oops sorry didn't see another page. T_T

L-Echo doesn't have in-game stage loading right now...I'm just focusing on the grids (holes/launchers) right now.  Sorry.

---

### Post by dudeofthedead on 2008-05-24
So you're saying there's only one riddle available at this time but can you at least manually switch to a new level?  What keys?

Are you the only person working on this project?

---

### Post by JT673 on 2008-05-24
Unfortunately, right now, yes T_T

When you start L-Echo, just give the filename.  The new releases have more than one XML file in its directory.  Just type:

```
./l-echo <file>
```

or else it will default to sample1.xml

---

### Post by JT673 on 2008-05-29
Bump

---

### Post by JT673 on 2008-05-30
In-game level loading, yay!

---

### Post by dudeofthedead on 2008-05-30
More sweetness!  \o/

And thanks for the e-mail, I will try that.

---

### Post by JT673 on 2008-06-11
bump

---

### Post by JT673 on 2008-08-13
> **JT673 said:**
> bump

indeed

---

### Post by dzark on 2009-01-12
Keep up the good work!

---


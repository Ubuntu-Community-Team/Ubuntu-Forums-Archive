---
title: "[SOLVED] python-opengl bindings"
date: 2008-12-16
forum: Gaming &amp; Leisure
---

### Post by RoseKnight on 2008-12-16
I'm trying to get these python/opengl bindings to work. 
(the test game I'm using to test the bindings is glChess)

Everytime I run the program, it'll say "starting chess" and then stop loading.

running it in a terminal gives this:

```

The program 'glchess' received an X Windo System error.
This probably reflects a bug in the program
The error was 'BadRequest (invalid request code or no such operation)'.
(Details: serial 108 error_code 1 request_code 143 minor_code 19)
(Note to programmers: -instructions for debug past this line-)

```

---

### Post by Perfect Storm on 2008-12-17
```
sudo apt-get install python-opengl
```

or search in synaptic package manager for "python opengl"

---

### Post by RoseKnight on 2009-01-02
Already did that... o_O

---

### Post by jpeddicord on 2009-01-02
**EDIT:** Never mind, I see you are just trying to run glChess. Ignore this, unless you are building a game.

I've never had a good experience with the Python OpenGL library. Try [Pyglet]("http://pyglet.org"), available as python-pyglet.

Once you open a pyglet window you can use whatever GL stuff you want. Just do a global import of Pyglet's OpenGL bindings:

```
from pyglet.gl import *
```

---

### Post by RoseKnight on 2009-01-03
this does nothing for me :(

however, I did find this bug report: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969)

which has a zillion duplicates. and seems to be exactly the problem I'm having. I just can't figure out what to do about it tho.

---

### Post by ShirishAg75 on 2009-01-04
One of the things I would say is if they are duplicate entries you are finding, see if they are linked together. If not, do the linking. The best way perhaps would be to go on IRC and talk with people in #ubuntu-bugs or #launchpad . Once they have that data (as to number of people suffering from that bug) and duplicates there is a higher chance of that bug getting attention.

---

### Post by RoseKnight on 2009-01-05
oh, it has plenty of entries, look for yourself.

Fortunately, I figure out how to get my particular problem corrected. :D

---


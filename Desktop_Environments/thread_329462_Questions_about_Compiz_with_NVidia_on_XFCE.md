---
title: "Questions about Compiz with NVidia on XFCE"
date: 2007-01-01
forum: Desktop Environments
---

### Post by c.dric on 2007-01-01
I just installed Compiz on XFCE using [this howto]("http://ubuntuforums.org/showthread.php?t=326592") and so far it worked quite well. i do have a few questions however ...

- I think i got most of the effects working properly, except that i can't zoom out of the cube as seen in [this pic]("http://go-compiz.org/index.php?title=Image:Cube.jpg"). I can zoom in and rotate the cube but no way to zoom out of the cube. is this a bug or i just haven't found the magic key yet ](*,) 

- It looks like i'm using Gnome themes for my windows' borders but where can i switch themes ? Do i need to install a program for this ?

- So far i've been using the compiz tray icon to start compiz in xfce ... but is there a way to load it automatically together with xfce ?

i will be grateful for any tips :) 

NB : For the record: i'm using a wacom tablet but it's doesn't seem to cause problems with the rest of the plugins so ...

---

### Post by c.dric on 2007-01-01
nevermind the first question ... it's not the zoom but the rotate plugin i had to experiment with.

....

what kind of picture do you need for the skydome ? mine don't seem to work.

---

### Post by c.dric on 2007-01-01
well, found the solution for the skydome ... on [the beryl forum]("http://forum.beryl-project.org/viewtopic.php?f=37&t=1556").

> Images used for the skydome have restrictions on resolution. Both horizontal and vertical resolution must be a power of 2. 512, 1024, 2048, 4096, are all acceptable values.

Note that there may be further restrictions on the maximum resolution you can use. Run "xvinfo | grep max" to see the max.



---

### Post by c.dric on 2007-01-01
How it looks like so far ...

[Capture 1]("http://c.dric.be/gium/misc/Compiz-cube1.jpg")
[Capture 2]("http://c.dric.be/gium/misc/Compiz-cube2.jpg")

---

### Post by SlCKB0Y on 2007-01-02
When I installed this, I had an annoying thing happen. The XFCE panels were slightly transparent without the mouse over them. With the mouse over them, they became completely opaque. 

I could not find a way to fix this. Using the state plugin worked for a while, but then it seemed to "forget" my settings.

---


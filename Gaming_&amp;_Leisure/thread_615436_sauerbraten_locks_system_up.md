---
title: "sauerbraten locks system up"
date: 2007-11-17
forum: Gaming &amp; Leisure
---

### Post by john_shaft on 2007-11-17
So I got sauerbraten all nice and installed finally after much searching for a .deb distribution or it, installs with out a hitch! But running it is another question.

When the program starts the screen flashes black then comes back to my desktop at a lower resolution, I don't see the game at all, and my system locks up.

Pretty new to this linux thing so I don't know how to make an event log(or the uBuntu equivalent) to track whats happening.  I am assuming that the 3d accelerator isn't starting from the flash of stark black folowed by a resized desktop(or so my now usless windows knowledge tells me)

feel free to chastise me for being a n00b [-o<

---

### Post by Casual Fan on 2007-11-18
Ditto. I get a brief game screen and some music plays...then all goes blank and the system locks up.

Help. I'll post whatever you need me to if you tell me how. :)

(noob too!)

UPDATE: It runs in a terminal just fine...hmmm. A puzzle, this thing called Linux.

---

### Post by danslinuxbox on 2007-11-22
sauerbraten needs quite a bit of power. try launching from a terminal with the -f option. it should run.

$cd sauerbraten/                        
$./sauerbraten_unix -f

---

### Post by Vadi on 2007-11-22
Usually the system locks up because of driver issues (I've been experiencing it).

What is your graphics card?

---


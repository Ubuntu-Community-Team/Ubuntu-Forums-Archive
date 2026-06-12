---
title: "would wine run the window game under &quot;BERYL&quot;"
date: 2007-04-27
forum: Gaming &amp; Leisure
---

### Post by mazingaz on 2007-04-27
I have read someone stating any window game running uder WINE will not work under the BERYL.  Is this true?
I have Xbuntu 7.04 (would this install beryl?)

---

### Post by cogadh on 2007-04-27
Beryl is a 3D graphics-accellerated window manager (see screenshot), it is not installed by default as part of Ubuntu (any flavor). It's not a good idea to try and run Windows games under Wine while running Beryl, it's too hard on the graphics card.

---

### Post by Ender Black on 2007-04-27
I play Eve Online with Beryl running with no issues at all... actually made it easier for me to run two characters on two different accounts.  Now that being said, Eve Online is terrible about utilizing the GPU and most of the processing is done onboard the CPU.. so Beryl and Eve Online are working from two different Processing pools.

---

### Post by Caseyjp on 2007-07-03
This screenshot of my desktop has two eve clients running:

[IMG]http://dl.eve-files.com/media/0703/transparent_cube.jpg[/IMG]

---

### Post by cogadh on 2007-07-03
No one ever said it couldn't be done, its just shouldn't be done. Even if you graphics card can handle the load of rendering the game and the 3D accelerated desktop at the same time, Beryl does funny things with windows and desktop spaces that can completely gack up a game. Generally speaking, it's not the desktop cube that will cause problems, its the window decorations and the create/minimize/maximize/close animations that are going to be a problem.

---

### Post by frodon on 2007-07-03
I tried with CS:S, it worked with a bit less performances so it will surely not be a problem with compiz-fusion new package (no need to use beryl anymore).

---

### Post by hikaricore on 2007-07-03
I wasn't aware that the new compiz/beryl merger was out yet. lol

---

### Post by cogadh on 2007-07-03
> **frodon said:**
> I tried with CS:S, it worked with a bit less performances so it will surely not be a problem with compiz-fusion new package (no need to use beryl anymore).
Isn't that a bit of an unfounded assumption? AFAIK, they haven't really announced what parts of Beryl are going to be merged with Compiz to make Compiz Fusion, beyond saying the "core components". For all we know, the additional eye-candy will be nearly the same and will have the same issues that Beryl had.

---


---
title: "PlanetPenguin Hamburger Hill"
date: 2005-11-26
forum: Gaming &amp; Leisure
---

### Post by Burgresso on 2005-11-26
Have you been able to conquer Hamburger Hill in planetpenguin racer? I can't pass this level. Any insight? :)

---

### Post by telmo on 2005-11-27
[QUOTE=Burgresso]Have you been able to conquer Hamburger Hill in planetpenguin racer? I can't pass this level. Any insight? :)[/QUOTE]

Neither can i...

---

### Post by Bazon on 2006-04-17
I had the same problems (that way I found that thread...)

But anyway, it's open source, so cheating is easy: :)

Just edit /usr/share/games/ppracer/courses/events/herring_run/event.tcl

in particular for Hamburger Hill:

from:
```
                    {

                        -course events/herring_run/hamburger_hill \

                                -name "Hamburger Hill" \

                                -description "Hamburger Hill is steep, narrow, twisty, lumpy, icy, and rocky, with a few trees right in your way!" \

                                -herring { 80 80 80 80 } \

                                -time { 220 215 210 205 } \

                                -score { 0 0 0 0 } \

                                -mirrored no -conditions cloudy \

                                -windy no -snowing no

                    }
```
to
```
                    {

                        -course events/herring_run/hamburger_hill \

                                -name "Hamburger Hill" \

                                -description "Hamburger Hill is steep, narrow, twisty, lumpy, icy, and rocky, with a few trees right in your way!" \

                                -herring { 70 70 70 70 } \

                                -time { 250 245 240 235 } \

                                -score { 0 0 0 0 } \

                                -mirrored no -conditions cloudy \

                                -windy no -snowing no

                    }
```
Or whatever time (in s) or herings you want... :)

Anyway, maybe a bug should be filed: "Planet Penguin too difficult for beginners or people who want to play just for fun..."

---

### Post by Burgresso on 2006-04-22
Very cool! Thanks Bazon....I'll file that bug...   ;)

---

### Post by benplaut on 2006-04-24
*i've* beaten it :D

/me basks in 15sec of fame

---


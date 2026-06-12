---
title: "swisswatch under launcher and gloobal menu"
date: 2014-09-04
forum: Desktop Environments
---

### Post by Azyx on 2014-09-04
Hey.
I want a analog desktop  clock.

Under 10.04LTS I used cairo-clock, but under 12.04LTS, it sometime freez, so I missed some busses and stuff.

When I upgraded to 14.04LTS, this happand again, so I installed the X11 clock:

sudo apt-get install swisswatch

Under 'Startup applications' i added:

name:  SwissWatch
command:  swisswatch -tick 1

But now the swisswatch appears in the upper left corner, but UNDER the  desktops global menu AND under the launcher so I can't reach swisswatch menu.
Does anyone know how I can move reach swisswatch menu, so I can set other preferenses, like 'show on all desktops, move it and stuff?

/Cheers

---

### Post by CantankRus on 2014-09-06
Try a conky analog clock.
[http://ubuntuforums.org/showthread.php?t=2166047&p=12749488#post12749488](http://ubuntuforums.org/showthread.php?t=2166047&p=12749488#post12749488)

[SIZE=3]or[/SIZE]

for swisswatch set the geometry.
eg
```
swisswatch -tick 1 -geometry 200x200-18+37
```

---


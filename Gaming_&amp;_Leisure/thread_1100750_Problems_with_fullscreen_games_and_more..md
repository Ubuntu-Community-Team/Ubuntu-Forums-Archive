---
title: "Problems with fullscreen games and more."
date: 2009-03-19
forum: Gaming &amp; Leisure
---

### Post by Frank-er on 2009-03-19
Anytime I play ANY game so far, after some time the game will come out of full screen and I have to minimize and then maximize it. Thats just a pain, but whatever.

Sometimes, often with Open Arena, I lose all control of the computer and have to reset it. Anyone know what happened? Any solutions?

Franker

---

### Post by hikaricore on 2009-03-19
You'll need to provide more info for anyone to be able to help.

Hardware, drivers, terminal output, etc.

---

### Post by Frank-er on 2009-03-19
Okay.

Hardware:

EVGA 650i Ultra Motherboard
EVGA 9600 GT Graphics Card
Intel E2200 PoS Processor :P 
4gig corsair dominator PC 6400 RAM
WD Caviar 250g 8MB Cache HDD
Liteon Sata DVD/CD 
Full SATA set up, works fine for every game I play in windows.
950 Watts total power in the system, so its not like the GPU is under nourished power wise.

Its odd like I'll play for 10-15 mins then boom, it comes out of fullscreen and I watch everything happen around me, But I lose control of the system.

---

### Post by Perfect Storm on 2009-03-19
Disable compiz.
Turn off screensaver.

---

### Post by Frank-er on 2009-03-19
Ugh, since I'm a total noob. What is compiz? And screensaver? By that you mean...the thing that comes on when the system idles for a certain amount of time?

---

### Post by Perfect Storm on 2009-03-19
> By that you mean...the thing that comes on when the system idles for a certain amount of time?

Yes.


Compiz is the 3D flashy thing on your Desktop. There are several ways to turn it on/off

1) Installing **fusion-icon** then you switch it with point'n'click


2) through commands in the terminal;

switch compiz off;
```
metacity --replace
```

switch compiz on;
```
compiz --replace
```

3) Install CompizConfig settings Manager
and enable "unredirect Fullscreen Windows" (under General). Then you can game with Compiz but you properly want to switch off screensaver.

---

### Post by Frank-er on 2009-03-19
> **Artificial Intelligence said:**
> Yes.


Compiz is the 3D flashy thing on your Desktop. There are several ways to turn it on/off

1) Installing **fusion-icon** then you switch it with point'n'click


2) through commands in the terminal;

switch compiz off;
```
metacity --replace
```

switch compiz on;
```
compiz --replace
```

3) Install CompizConfig settings Manager
and enable "unredirect Fullscreen Windows" (under General). Then you can game with Compiz but you properly want to switch off screensaver.

This worked, thanks!!

---

### Post by mocoloco on 2009-03-19
You forgot the easiest way, System -> Preferences -> Appearance. Visual Effects tab, set to "None".

---


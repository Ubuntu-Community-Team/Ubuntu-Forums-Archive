---
title: "Very Strange Half Life 2..."
date: 2006-06-15
forum: Gaming &amp; Leisure
---

### Post by Wallakoala on 2006-06-15
So I am getting half life 2 soon, and I decided to try the demo out under WINE.

I followed this guide to install steam: [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam)

And steam works fine. I can play counterstrike 1.6 perfectly as well.

So I have steam download the hl2 demo, and decide to give it a whirl.
I have the following script set to run the demo:
```
#!/bin/bash
WINEDEBUG=-all wine C:/Program\ Files/Steam/Steam.exe -fullscreen \
    -width 1080 -height 1024 -applaunch 219 \
    -heapsize 512000 +map_background none "$@"

```

I know this works because if I change the "applaunch 219" with "applaunch 10", counterstrike runs (not counterstrike source).

So then I run the game, and it starts up very slowly for some reason. Finally, it gets to the main menu. I click "new game" and then start the first level. After a very long loading time, I finally get into the game.

View the attached screenshots, they speak for themselves.
(Note: In the screenshots I am running the game in a virtual desktop. I also tried running it fullscreen and I get the same results)

This isn't a hardware problem because I have a pretty nice computer (see sig). I have played it succesfully on windows before with this machine.

EDIT: Forgot to say that the game actually runs pretty smooth, but...yeah...it is kinda screwed up

---

### Post by echo $USER on 2006-06-15
You should be advised that Source games run like crap on Wine.  I have a evga 6800gs co, P4 3.0, 1gb corsair xms, and it runs like crap on mine too.   Just be glad they run at all.  But CS 1.6 and DOD run wonderfully.

---

### Post by Wallakoala on 2006-06-15
[QUOTE=echo $USER]You should be advised that Source games run like crap on Wine.  I have a evga 6800gs co, P4 3.0, 1gb corsair xms, and it runs like crap on mine too.   Just be glad they run at all.  But CS 1.6 and DOD run wonderfully.[/QUOTE]

Does it look like that on yours too?

btw I love your avatar :D

---

### Post by Alienist on 2006-06-15
Those screenshots look like HL2 is running under DX7. For some reason maybe DX9 is not enabled under your configuration or something.

---

### Post by Wallakoala on 2006-06-15
[QUOTE=Alienist]Those screenshots look like HL2 is running under DX7. For some reason maybe DX9 is not enabled under your configuration or something.[/QUOTE]

How would I change that?

---

### Post by echo $USER on 2006-06-15
[QUOTE=Alienist]Those screenshots look like HL2 is running under DX7. For some reason maybe DX9 is not enabled under your configuration or something.[/QUOTE]

yeah, how do we change that?  Mine looks just like the og poster.

---

### Post by ubu-for on 2006-06-16
[QUOTE=Wallakoala]So I am getting half life 2 soon, and I decided to try the demo out under WINE.

I followed this guide to install steam: [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam)

And steam works fine. I can play counterstrike 1.6 perfectly as well.

So I have steam download the hl2 demo, and decide to give it a whirl.
I have the following script set to run the demo:
```
#!/bin/bash
WINEDEBUG=-all wine C:/Program\ Files/Steam/Steam.exe -fullscreen \
    -width 1080 -height 1024 -applaunch 219 \
    -heapsize 512000 +map_background none "$@"

```

I know this works because if I change the "applaunch 219" with "applaunch 10", counterstrike runs (not counterstrike source).

So then I run the game, and it starts up very slowly for some reason. Finally, it gets to the main menu. I click "new game" and then start the first level. After a very long loading time, I finally get into the game.

View the attached screenshots, they speak for themselves.
(Note: In the screenshots I am running the game in a virtual desktop. I also tried running it fullscreen and I get the same results)

This isn't a hardware problem because I have a pretty nice computer (see sig). I have played it succesfully on windows before with this machine.

EDIT: Forgot to say that the game actually runs pretty smooth, but...yeah...it is kinda screwed up[/QUOTE]


[http://ubuntuforums.org/showthread.php?t=176975](http://ubuntuforums.org/showthread.php?t=176975)

Disable pixelshaders in winecfg! :cool:

---

### Post by echo $USER on 2006-06-16
thanks ubu-for.

---

### Post by bruce89 on 2006-06-16
[QUOTE=edmond]so that is very strange maby its bicous of the "We Be 1"[/QUOTE]
That is not good enough.  I won't get you banned if you can tell me what Ubuntu is.

Everyone else - see here - [http://www.ubuntuforums.org/showthread.php?t=197927](http://www.ubuntuforums.org/showthread.php?t=197927)

---

### Post by RavenOfOdin on 2006-06-16
[QUOTE=bruce89]
Everyone else - see here - [http://www.ubuntuforums.org/showthread.php?t=197927](http://www.ubuntuforums.org/showthread.php?t=197927)[/QUOTE]

What the heck?!?

LOL

---

### Post by echo $USER on 2006-06-16
[QUOTE=bruce89]That is not good enough.  I won't get you banned if you can tell me what Ubuntu is.

Everyone else - see here - [http://www.ubuntuforums.org/showthread.php?t=197927](http://www.ubuntuforums.org/showthread.php?t=197927)[/QUOTE]

Waht does that have to do w/ CS:S and wine?

---


---
title: "OpenArena - low fps"
date: 2009-04-02
forum: Gaming &amp; Leisure
---

### Post by R33D3M33R on 2009-04-02
I tried OpenArena 0.8.1 and it kind of dissapointed me. Altough its based on Quake 3 engine (Quake 3 Arena runs with about 100FPS on standard maps) it seems to be way slower. For example: i get from 30-60 FPS on Sago Castle, but the map is really tiny, there are no large areas, water etc. I can't even get stable FPS over 100 by looking at walls! Everything is set to low, resolution to 640x480 and I just can't think of another way to speed up Open Arena.

My PC is Athlon 1800+,768MB RAM and Geforce 4 Ti 4200 128MB

Thank you in advance!

---

### Post by 5nak3 on 2009-04-02
have you made sure you have the right drivers for you graphics card? that seems to be the first problem with a lot of Linux game.

Maybe turn off any compiz effect you may be running. Check if direct rendering is working

glxinfo if I am not mistaken and the third line from the output should say direct rendering: yes

That should be a start until someone with more knowledge comes along.

---

### Post by R33D3M33R on 2009-04-02
I have 96.43.11 installed and direct rendering works, I'm also not running compiz.

---

### Post by racerraul on 2009-04-02
Is direct rendering better than OpenGL?
Have you tried a later driver release?

---

### Post by R33D3M33R on 2009-04-02
Hm, I think direct rendering only means the OpenGL acceleration works OK.
There are no newer driver this is the latest.

I have also tried Warsow and it runs better on higher settings (the fps stays at about 90, there are no drops under 60 FPS). I guess OpenArena is just not optimised enough?

---

### Post by eragon100 on 2009-04-02
> **R33D3M33R said:**
> Hm, I think direct rendering only means the OpenGL acceleration works OK.
There are no newer driver this is the latest.

I have also tried Warsow and it runs better on higher settings (the fps stays at about 90, there are no drops under 60 FPS). I guess OpenArena is just not optimised enough?

I think it's because it uses an improved version of the Quake 3 engine.
Often, improved graphics means less performance. But this is just a taught.

And yeah, it probable isn't optimised very well either since it's not finished yet and as far as I know there is only one programmer.

---

### Post by racerraul on 2009-04-02
> **R33D3M33R said:**
> I have 96.43.11 installed.

Is that the Driver Version you are using?

I am using 180.11, but I do have a much newer card.

---

### Post by R33D3M33R on 2009-04-03
> **racerraul said:**
> Is that the Driver Version you are using?

I am using 180.11, but I do have a much newer card.

Yes it is. I have to use the legacy driver because the graphics card is very old.

As for OpenArena, I have found some tweaks for the game here: [http://openarena.wikia.com/wiki/Tweak](http://openarena.wikia.com/wiki/Tweak)
I hope they will help.

---

### Post by R33D3M33R on 2009-04-03
I have also tweaked the sound as described here:
[http://ubuntuforums.org/showthread.php?t=458077](http://ubuntuforums.org/showthread.php?t=458077)

And the OA benchmark now 
[http://dri.freedesktop.org/wiki/Benchmarking](http://dri.freedesktop.org/wiki/Benchmarking)
outputs ~100FPS, it was ~80 FPS before. A huge improvement :)

---


---
title: "can't play a bunch of games"
date: 2009-03-22
forum: Gaming &amp; Leisure
---

### Post by zpweston on 2009-03-22
every time i try to open games like tremulous, frets on fire, alien arena and open arena they go to the menu but i can't see any options. like my screen is scrambled and pixelate. I assume it's something with my resolution or graphics, i mean i cant really play any game in full screen so what do i do. i'm sure there's an easy fix. is there any way to keep those games from going into full screen. like i play plane shift in the next size down from full screen and it's fine.

---

### Post by zpweston on 2009-03-22
is there any way to just keep the games from going into full screen

---

### Post by SunnyRabbiera on 2009-03-22
Native linux games can be tricky, some are better then others.
Usually though linux isnt that good with games, too bad as its a major thing most people use on their computers.

---

### Post by disturbedite on 2009-03-22
it is often possible to change options in programs' config files independently of the program. maybe try poking around them and see if you can run them in software mode as opposed to opengl.

also, check if direct rendering is enabled:

```
glxinfo | grep direct
```

---

### Post by zpweston on 2009-03-22
my direct enabling is rendered, the only problem is is that all the games are in applications/games do you. So how do i change settings on pre installed games

---

### Post by hikaricore on 2009-03-22
> **SunnyRabbiera said:**
> Native linux games can be tricky, some are better then others.
Usually though linux isnt that good with games, too bad as its a major thing most people use on their computers.

Please refrain from posting garbage like this.

---

### Post by Bölvaður on 2009-03-23
you might not have your graphics set up correct.

please enter this into the terminal (applications &#8594; accessories &#8594; terminal)

glxgears



and the output in the terminal should be something like:
33008 frames in 5.0 seconds = 6601.416 FPS

you can close the gear window in 10-15 seconds. You probably need more than 300 fps in glxgears to play any games without problems.

---

### Post by darthmob on 2009-03-23
try hitting alt + enter to switch between windowed and fullscreen mode when running openarena (I guess this works with all idtech games like urban terror, ETQW, quake3/4, doom3 etc.).

---

### Post by MrYuck on 2009-06-15
I'm having the same problem as zpweston, I've tried everything suggested above.

Direct rendering is enabled

When i did the 'glxgears' thing i got (a sample line)

       3106 frames in 5.0 seconds = 621.190 fps

and the alt + thing didn't seem to work.

Any ideas or advice would be greatly appreciated.

---

### Post by wingnux on 2009-06-15
Posting your system specs (mainly your gfx card) would be of HUGE help...

---

### Post by MrYuck on 2009-06-16
I figured it out kind of, if i turn off visual effects it works fine, but its a hassle to have to do that every time i play a game, is there a way to fix this or make it so that visual effects automatically turn off when the desktop isn't shown


and i'm using a macbook 4,1 
2.4 GHz intel duo
intel gma X3100 integrated graphics
2 gigs of ram
running 8.10 Intrepid

---

### Post by Grishka on 2009-06-18
> **MrYuck said:**
> I figured it out kind of, if i turn off visual effects it works fine, but its a hassle to have to do that every time i play a game, is there a way to fix this or make it so that visual effects automatically turn off when the desktop isn't shown


and i'm using a macbook 4,1 
2.4 GHz intel duo
intel gma X3100 integrated graphics
2 gigs of ram
running 8.10 Intrepid

try [this](http://ubuntuforums.org/showthread.php?t=1157516&highlight=compiz+game+script).

---

### Post by jacksaff on 2009-06-18
> **MrYuck said:**
> 
When i did the 'glxgears' thing i got (a sample line)

       3106 frames in 5.0 seconds = 621.190 fps



That's very low and you will struggle to play a lot of games even on low quality settings and low resolution. The games on this thread generally need middle-of-the-range graphics cards to run properly.

---


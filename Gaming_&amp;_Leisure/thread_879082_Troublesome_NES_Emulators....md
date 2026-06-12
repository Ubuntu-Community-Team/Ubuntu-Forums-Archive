---
title: "Troublesome NES Emulators..."
date: 2008-08-03
forum: Gaming &amp; Leisure
---

### Post by mishathegoat on 2008-08-03
Hey everyone,
I dunno what it is but I can't seem to get any NES emulators working properly. FCEU is **VERY** slow though I'm not sure why, and Megnafen has a horrible joystick delay (again, I'm not sure why).

Any advice, help, or suggestions? I'm not so good at compiling things.

gfceu isn't an option because it is windowed.. I'll be running it through mythtv

---

### Post by FranMichaels on 2008-08-03
Without knowing the hardware you have, I'd guess that you don't have opengl acceleration.

```
glxinfo | grep direct
```

If it doesn't return yes, either install the proper driver if available, or 

Try changing mednafen to sdl (software rendering) instead of opengl in ~/.mednafen/mednafen.cfg

Search for the line
vdriver 0

make it 

vdriver sdl

See if that takes care of the delay.

---

### Post by mishathegoat on 2008-08-03
Thanks that seemed to speed things up quite a bit. It works almost flawlessly now. However the screen get a *little* jitter if I walk/run fast (Testing with Super Mario Bros, [I own the game]). Any other tips to speed things up just a tad bit more? Here is the command I'm using to start the rom.

```
mednafen -nes.no8lim 1 -nes.clipsides 1 -nes.stretch 1 -nes.xres 640 -nes.yres 480 -vdriver sdl SuperMarioBros.nes
```

---

### Post by FranMichaels on 2008-08-04
I'm glad that helps. You could try lowering the resolution (I'm lazy so I just edit the mednafen.cfg rather than pass parameters). The original res is 256 x 224 (well 240 actually, but 8 bottom and top lines didn't display on most TV's) Try that and see if the video card handles the res.

Now, if the tearing you are getting only occurs when with swift movement left or right... It's due to not vertical syncing (has to do with refresh rate not matching the tv.)

Good news and bad news. I know the fix when it's using opengl acceleration. Install driconf, and choose force vertical retrace (or some similar option.)

Using software rendering, only matching the refresh rate (60hz?) would make it tear free...

What hardware, specifically video card do you have? If there is a driver (preferably an open source one) that would let you get direct rendering, you' be golden.

Good luck!

---

### Post by tuxxy on 2008-08-04
snes9express is in the repos, works fine

---

### Post by FranMichaels on 2008-08-04
> **tuxxy said:**
> snes9express is in the repos, works fine

That is an [snes]("http://en.wikipedia.org/wiki/Snes") emulator, not [nes]("http://en.wikipedia.org/wiki/Nintendo_Entertainment_System").

---

### Post by BigSilly on 2008-08-04
For NES you're better off with Mednafen and it's front end. Both are available on this forum. Do a search and they should turn up. Mednafen's NES emulation is fantastic, and with the GUI that a forumite has made it's even better. I don't use anything else.

---

### Post by disturbedite on 2008-08-04
i have to disagree. the best NES emulator is Nestopia.

---

### Post by Mednafen on 2008-08-04
> **mishathegoat said:**
> Hey everyone,
I dunno what it is but I can't seem to get any NES emulators working properly. FCEU is **VERY** slow though I'm not sure why, and Megnafen has a horrible joystick delay (again, I'm not sure why).


What joystick do you use?

---

### Post by 1337 on 2008-08-05
I think best combo for emulating nes is mednafen emulator + [mednafenfe]("http://mednafenfe.sourceforge.net") frontend. It's fas, looks good and it's easy.

Regards

---

### Post by BigSilly on 2008-08-05
> **disturbedite said:**
> i have to disagree. the best NES emulator is Nestopia.

NEStopia is pretty cool, but to be fair it isn't really different enough to Mednafen in its NES emulation to warrant recommending to someone that they attempt installing it - especially if they're new to Linux. And the OP did state that he's not so good at compiling things. I myself did compile the recent version of NEStopia, but to be honest I still prefer to use Mednafen at the moment. Not only is there a fab GUI doing the rounds as has already been linked to above, but it can also emulate other systems too, so you don't have to switch emulators if you want to play PC Engine or SMS. It's brilliant, and getting better all the time.

But I'm not dissing NEStopia. I'll just be much happier with it when they make a proper Linux package. You can't deny it can be a bit of a pain to put together, especially for the newcomer!

---


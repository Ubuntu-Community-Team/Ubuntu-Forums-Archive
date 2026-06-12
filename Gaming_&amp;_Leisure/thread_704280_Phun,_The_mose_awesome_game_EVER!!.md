---
title: "Phun, The mose awesome game EVER!!"
date: 2008-02-22
forum: Gaming &amp; Leisure
---

### Post by Muscar on 2008-02-22
Phun is a Master of Science Theises by Computing Science student Emil Ernerfeldt for supervisor Kenneth Bodin at VRLab, Umeå University. The solver is based on work by Claude Lacoursière

Phun is meant to be a playground where people can be creative. It can also be used as an educational tool to learn about physics concepts such as restitution and friction.

Phun was coded in C++ using OpenGL, GLEW, SDL (for window management), SDL_image (for reading images) and boost, including boost_filesystem. Everything was coded by me, including the physics engine and user interface. 


**Youtube video:**
[http://www.youtube.com/watch?v=0H5g9VS0ENM](http://www.youtube.com/watch?v=0H5g9VS0ENM)

**Images:**
[IMG]http://www.acc.umu.se/~emilk/screenshots/phun_080212_0001.png[/IMG]

[IMG]http://www.acc.umu.se/~emilk/screenshots/phun_080212_0002.png[/IMG]

**Download link:** [http://www.acc.umu.se/~emilk/downloads.html](http://www.acc.umu.se/~emilk/downloads.html)
(It works perfectly on linux)

**Some good things to know:**

While using the brush tool, press and hold shift to make straight lines

If the game crashes all the time, or even won't load delete the Shaders folder.

You can find more by pressing Help! in the game

*Please contribute your own makings so we can try them out!*

Here is one of mine:

[img]http://i101.photobucket.com/albums/m47/Muscar/phun_brick_house1.png[/img]

Download: [http://www.megaupload.com/?d=TESROYTE](http://www.megaupload.com/?d=TESROYTE)
 (put the save in your Scenes folder)

---

### Post by Cappy on 2008-02-22
This looked really cool so I tried it but I'm getting a core dump. It is probably because of my laptop's Intel 945 GSM.

```

-----------------------------
  Phun beta 3.0
  February 22 2008, 09:25:53
-----------------------------
09:25:53: Init SDL...
09:25:54: Application created
09:25:54: Parsing autoexec.cfg...
09:25:54: Creating window...
09:25:54: Destroying GL resources
09:25:54: Setting up SDL
09:25:54: Setting video mode
09:25:54: Init GLEW...
09:25:54: Setting vsync
09:25:54: Setting viewport
09:25:54: Checking for alpha framebuffer
09:25:54: Checking for shader support
09:25:54: Loading all resources...
09:25:54: Reloading N9rendering7TextureE
09:25:54: Reloading N9rendering6ShaderE

```

I'll try it on my desktop later (nvidia 7 series)

---

### Post by acoustibop on 2008-02-22
Heh, heh, Tuxor actually posted [your game]("http://ubuntuforums.org/showthread.php?t=702674") here about a day ago, Muscar! ;)

---

### Post by ad5665 on 2008-02-22
good find using on windows and it works great

---

### Post by Vadi on 2008-02-22
I love this

---

### Post by Cappy on 2008-02-22
So, I'm back at my desktop.

It turns out the 64-bit version isn't linked well.
Now that I have it working on one computer .. I should say that this is possibly the coolest thing EVER. Except Batman. And the Green Lantern. This application is AMAZING!

Edit: Add the 64-bit libGLEW.so.1.5 and libboost_filesystem.so in the 64-bit package please?

---

### Post by Vadi on 2008-02-22
I had that problem too, but I got the libglew-1.5 package from synaptic, and it worked.

I guess one of the 3rd party repositories I signed up for has it.

---

### Post by Muscar on 2008-02-22
> **acoustibop said:**
> Heh, heh, Tuxor actually posted [your game]("http://ubuntuforums.org/showthread.php?t=702674") here about a day ago, Muscar! ;)

But that thread didn't really have any info on the game, and i think it would be nice for people to post things they have done

---

### Post by matthewcraig on 2008-02-22
> **Vadi said:**
> I had that problem too, but I got the libglew-1.5 package from synaptic, and it worked.

You'll get the error *error while loading shared libraries: libGLEW.so.1.5* when trying to run this program with Gutsy.

Ubuntu Gutsy comes with v 1.4 of GLEW, but you don't need to override this library!!  The Phun download comes with the correct version.

Just run the program with this command line:

```
LD_LIBRARY_PATH=. ./phun
```

FYI, 08.04 will have v 1.5

---

### Post by yabbadabbadont on 2008-02-22
No source, no care.  ;)

---

### Post by Cappy on 2008-02-22
> **matthewcraig said:**
> You'll get the error *error while loading shared libraries: libGLEW.so.1.5* when trying to run this program with Gutsy.

Ubuntu Gutsy comes with v 1.4 of GLEW, but you don't need to override this library!!  The Phun download comes with the correct version.

Just run the program with this command line:

```
LD_LIBRARY_PATH=. ./phun
```

FYI, 08.04 will have v 1.5

Thanks, I completely looked over that.

---

### Post by meborc on 2008-02-23
just here to say THANKS... now i will never get my lab-reports done on time :D

great game!

---

### Post by cdaringe on 2008-02-28
cdaringe@cdcraptop:~/Desktop/Phun$ LD_LIBRARY_PATH=. ./phun

!! ERROR: Exception caught: Couldn't init SDL: No available video device

Major bummer!   Ah, it could be so many things!

---

### Post by grossaffe on 2008-02-28
> **meborc said:**
> just here to say THANKS... now i will never get my lab-reports done on time :D

great game!

i hear that, i'll be too busy with a physics simulation to finish my physics lab reports. :mad:

---


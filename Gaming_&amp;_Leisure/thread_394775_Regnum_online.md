---
title: "Regnum online"
date: 2007-03-27
forum: Gaming &amp; Leisure
---

### Post by Flying George on 2007-03-27
I downloaded Regnum Online, hearing only great things about the game. I installed it and made a profile on the site. I then installed the game, changed the language to English and when I click play my cursor moves up to the corner of the screen and the game fails to launch. My system requirements are not the problem, but I will list them anyway to prove it. (I am able to play ET, TC:E and Warsow without a hitch)

AMD Athlon XP 2200+ processor (1.8 GHZ)
512 MB RAM 
ATI Radeon 9000 pro 128 MB DDR RAM operates at apprx: 400-600 MHZ
120 GB of HDD space partitioned to Ubuntu

That's about it, I know it's not the best, but its enough. Any help is appreciated. And a pre-emptive 'Thank you' to all those that do help :)

-Gene

---

### Post by Iarwain ben-adar on 2007-03-27
Hi,

can you try to run it via terminal? That could give us some errors to start with...

I play it aswell xD


Iarwain

---

### Post by Flying George on 2007-03-27
Okay, this is what i get:

Pure Virtual method called
terminate called without an active exception
Aborted (core dumped)

---

### Post by Iarwain ben-adar on 2007-03-27
Strange error..

Don't know a thing about it :D

Did you try a search on their forum?


Iarwain

---

### Post by Flying George on 2007-03-27
Oh noes. I just made an attempt to upgrade my Graphic drivers and now nothing will start for me :( So, I don't know what to do...I'm very close to reinstalling ubuntu.

---

### Post by Perfect Storm on 2007-03-27
Do a
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Restart X <ctrl>+<alt>+<backspace>

---

### Post by Flying George on 2007-03-27
THANK YOU, AI!! You have saved me! =D> :biggrin:

---

### Post by Flying George on 2007-03-27
After I used AI's method to reset whatever it was I reset. I attempted once more to launch Regnum (from the terminal) I no longer get an error. However, it still fails to launch. A rather curious predicament.

---

### Post by hikaricore on 2007-03-27
Any new errors or the same ones?

---

### Post by Flying George on 2007-03-27
I have been getting a common error, throughout the course of the day i have been carousing about on these forums reading peoples thoughts on good games, and downloading said games, thank you good people of the forums. And this is the common error I have received among all the games I could not get to work: 

Error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory.

once again, any help is good.

---

### Post by Perfect Storm on 2007-03-27
```
sudo aptitude install libsdl-image1.2
```

---

### Post by Flying George on 2007-03-27
I have a slightly new error:

error while loading shared libraries: libSDL_mixer-1.2.so.0: cannot open shared object file: no such file or directory.

---

### Post by Perfect Storm on 2007-03-27
Now guess/try install it as I have shown ;)

hint, you can also use synaptic if you unsure what the name is specific.

---

### Post by Flying George on 2007-03-27
Thank you again AI. YOU HAVE SAVED MY DAY TWICE TODAY, I could hug you! But, sauerbraten froze Ubuntu....I'll work on that. And Regnum STILL doesn't launch :confused: I don't get it.

---

### Post by Perfect Storm on 2007-03-27
Check regnum howto in Ubuntu Gamers Arena, you might have miss something.

---

### Post by Flying George on 2007-03-27
Far as I can tell I missed nothing. I'll do some more research. Dave GNUkem works ^^ I'll play around with everything else. Thank you for all your help, You've all been wonderful.

---

### Post by hikaricore on 2007-03-28
Have you installed the libSDL libraries?

Check the the output if any of:

```
ls /usr/lib/libSDL_*
```

For any missing libraries you're getting in errors.

For example I get:

> 
libSDL-1.2.so.0        libSDL_gfx.so              libSDL_image.la            libSDL_mixer.la          libSDL_Pango.so.1          libSDL_ttf-2.0.so.0
libSDL-1.2.so.0.7.3    libSDL_gfx.so.13           libSDL_image.so            libSDL_mixer.so          libSDL_Pango.so.1.1.0      libSDL_ttf-2.0.so.0.6.2
libSDL.a               libSDL_gfx.so.4            libSDL.la                  libSDL_net-1.2.so.0      libSDL.so                  libSDL_ttf.a
libSDL_console.so.1    libSDL_gfx.so.4.9.0        libSDLmain.a               libSDL_net-1.2.so.0.0.5  libSDL_sound-1.0.so.1      libSDL_ttf.la
libSDL_console.so.1.3  libSDL_image-1.2.so.0      libSDL_mixer-1.2.so.0      libSDL_net.a             libSDL_sound-1.0.so.1.0.0  libSDL_ttf.so
libSDL_gfx.a           libSDL_image-1.2.so.0.1.4  libSDL_mixer-1.2.so.0.2.4  libSDL_net.la            libSDL_ttf-1.2.so.0
libSDL_gfx.la          libSDL_image.a             libSDL_mixer.a             libSDL_net.so            libSDL_ttf-1.2.so.0.2.0


You may need to open synaptic package manager and search for libsdl and install the correct libraries.

**edit** I just noticed this had a second page, lol I was replying from one page back.  :P  sorry

---

### Post by Flying George on 2007-03-30
Do'nt worry about it

Someone else might benefit from that. Good Work!

---

### Post by queso_lg on 2007-11-22
Hi people.. i recentrly installed ubuntu Gutsy Gibbon 7,10 on my computer and i come from XP!!!.. i been trying to install Regnum for about 2 days now reading every post that i found.. this was the closest one to get it working. After i did a sudo dpkg-reconfigure -phigh xserver-xorg.. as AL said i found a new error:

b7f93000-b7fad000 r-xp 00000000 03:02 750721     /lib/ld-2.6.1.so
b7fad000-b7faf000 rw-p 00019000 03:02 750721     /lib/ld-2.6.1.so
bfb67000-bfb7b000 rwxp bfb67000 00:00 0          [stack]
bfb7b000-bfb7d000 rw-p bfb7b000 00:00 0 
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Cancelado (core dumped)

this is where it stops... any suggestions?? please!!:confused:

---

### Post by MarqX on 2007-11-30
Try this
MALLOC_CHECK_=0 ./rolauncher

---


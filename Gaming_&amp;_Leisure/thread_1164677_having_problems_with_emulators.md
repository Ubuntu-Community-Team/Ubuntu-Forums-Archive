---
title: "having problems with emulators"
date: 2009-05-19
forum: Gaming &amp; Leisure
---

### Post by Moonsocket on 2009-05-19
im new to ubuntu and everything but im having problems with nes and snes emulators im useing snes9x express and gfce ultra they are extreamly laggy and freeze randomly any way to fix this or any better emulators would help

---

### Post by Dark Aspect on 2009-05-19
> **Moonsocket said:**
> im new to ubuntu and everything but im having problems with nes and snes emulators im useing snes9x express and gfce ultra they are extreamly laggy and freeze randomly any way to fix this or any better emulators would help

Are your video drivers installed? Also zsnes is far superior to that of snes9x.

---

### Post by yoasif on 2009-05-19
zsnes (in repos) and snes9x-gtk ([ppa]("https://launchpad.net/~bearoso/+archive/ppa")) are the best, imo.

---

### Post by Dark Aspect on 2009-05-20
> **yoasif said:**
> zsnes (in repos) and snes9x-gtk ([ppa]("https://launchpad.net/~bearoso/+archive/ppa")) are the best, imo.

Actually, zsnes is only in the repositories if he is using the i386 architecture, for 64-bit users go [here]("http://www.megaupload.com/?d=IUNWPS12").

---

### Post by Moonsocket on 2009-05-20
> **Dark Aspect said:**
> Are your video drivers installed? Also zsnes is far superior to that of snes9x.

how do i kno if they are/ how do i install them 
and ive never been a fan of znes is too messy i guess

---

### Post by Dark Aspect on 2009-05-20
> **Moonsocket said:**
> how do i kno if they are/ how do i install them 
and ive never been a fan of znes is too messy i guess

Well there are two ways to find out if you have a video driver installed. One you can type in to the terminal:

```
glxinfo | grep render
```

and that should give, if you have drivers properly installed

```
direct rendering: Yes
```

Or you can go to System>>>Administration>>>Hardware Drivers

That hardware tab should also be where you can install your video driver depending in what kind of card you use.

---

### Post by javyn999 on 2009-05-20
ZNES runs great for me.  In all these emulators you can go to video options and enable OpenGL rendering.  Won't make things look any better of course, but may help the lag issue.

Oh, and as far as NES emulating goes, it has ALWAYS lagged for me.  NES roms lagged 10 years ago when I was emulating them on Windows, and they lag today in Ubuntu even though I have a Geforce 6200 256meg video card.

I don't think there's anything you can do there.  Even NES Tetris lags me.  And I've tried varying releases of every NES emulator out there.

---

### Post by Moonsocket on 2009-05-20
> **Dark Aspect said:**
> Well there are two ways to find out if you have a video driver installed. One you can type in to the terminal:

```
glxinfo | grep render
```and that should give, if you have drivers properly installed

```
direct rendering: Yes
```Or you can go to System>>>Administration>>>Hardware Drivers

That hardware tab should also be where you can install your video driver depending in what kind of card you use.
ya it works apparently but every 3d program i run makes a static line down the middle and lagfest everything worked fine when i had windows on my computer but im going to do everything i can to fix things in linux im not going back to windows

---

### Post by BoyOfDestiny on 2009-05-20
> **Moonsocket said:**
> ya it works apparently but every 3d program i run makes a static line down the middle and lagfest everything worked fine when i had windows on my computer but im going to do everything i can to fix things in linux im not going back to windows

It's probably the video drivers. Have you tried turning off Visual Effects in System -> Preferences -> Appearance.

I have 0 lag in zsnes (the correct spelling for those wanting the package) and sdlmess and mednafen (but if you enable vsync, unless your monitor has the same refresh-rate as a tv, it will not be as snappy as the original systems.)
I used them an old ati 9250 and now on various onboard intel chips (open source drivers in every case.) 

Lastly, what video card do you have, maybe someone can offer advice or a tweak.

I admire your determination to not give up on Linux when running into a few hiccoughs.

---

### Post by Moonsocket on 2009-05-20
> **BoyOfDestiny said:**
> It's probably the video drivers. Have you tried turning off Visual Effects in System -> Preferences -> Appearance.

I have 0 lag in zsnes (the correct spelling for those wanting the package) and sdlmess and mednafen (but if you enable vsync, unless your monitor has the same refresh-rate as a tv, it will not be as snappy as the original systems.)
I used them an old ati 9250 and now on various onboard intel chips (open source drivers in every case.) 

Lastly, what video card do you have, maybe someone can offer advice or a tweak.

I admire your determination to not give up on Linux when running into a few hiccoughs.
turning of visual effects did the trick for the lag but im still haveing probs with 3d programs like frets on fire or glest but thanks man

---


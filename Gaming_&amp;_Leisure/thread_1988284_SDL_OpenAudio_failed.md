---
title: "SDL_OpenAudio failed"
date: 2012-05-27
forum: Gaming &amp; Leisure
---

### Post by williammartindale on 2012-05-27
Im trying to run a game postal2... it runs but I get no sound. I get the following error.

```
rex@N55SF:~/postal2$ ./postal2
Postal 2
Copyright 2003 Running With Scissors, Inc.
Unreal Engine
Copyright 2001 Epic Games, Inc.
*AL lib*: *sdl.c:208*: SDL_OpenAudio failed: No available audio device
```I have the most resent open audio library installed

Im running Ubuntu 12.04 64bit

It ran fine under Ubuntu 11.04 64bit

---

### Post by DoktorSeven on 2012-05-27
Have you tried disabling PulseAudio?  PA is nothing but a headache and a problem for me (your experience may differ) and I've benefited immensely by just removing it completely -- at the very least you can try killing the process and try running the game without.

---

### Post by williammartindale on 2012-05-28
Ill give that a try when I get home.

---

### Post by williammartindale on 2012-05-29
I tried killing pulseaudio but as soon as I start the game Pulseaudio starts back up.

---

### Post by thatguruguy on 2012-05-29
Try the following:
```
padsp ./postal2
```

That will route the OpenAudio call through pulseaudio.

---


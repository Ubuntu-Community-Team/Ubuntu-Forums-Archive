---
title: "Enemy Territory Problem!"
date: 2005-11-11
forum: Gaming &amp; Leisure
---

### Post by Spac on 2005-11-11
I'm having a slight problem with the free Wolfenstine based game Enemy Territory, every time I start the game, all I get is a black screen, at first I thought it was just loading, but I left it for 15mins and nothing had changed.

I just recently installed the latest NVIDIA Drivers for my 6600GT (my system specs are in my signature below).

I'm using the x86 version of Ubuntu 5.04 since the AMD64 version was incompatible with a few programs.

-Spac

---

### Post by gerbman on 2005-11-11
[QUOTE=Spac]I'm having a slight problem with the free Wolfenstine based game Enemy Territory, every time I start the game, all I get is a black screen, at first I thought it was just loading, but I left it for 15mins and nothing had changed.

I just recently installed the latest NVIDIA Drivers for my 6600GT (my system specs are in my signature below).

I'm using the x86 version of Ubuntu 5.04 since the AMD64 version was incompatible with a few programs.

-Spac[/QUOTE]

Are you starting it from the terminal?  If not, try doing that and check the output messages as it starts up.  A common problem is that it can't acquire the needed sound device and just hangs.  Quit any application that might be using the sound device, or run ```
pkill esd
``` before starting the game.  ESD can be started again with ```
esd &
```

---

### Post by Spac on 2005-11-12
Thanks, I'll try that as soon as I get back on my pc. I'd like to get some games running on Linux, because I'm thinking about completley switching over, I dont know if I can survive another Windows release.

---


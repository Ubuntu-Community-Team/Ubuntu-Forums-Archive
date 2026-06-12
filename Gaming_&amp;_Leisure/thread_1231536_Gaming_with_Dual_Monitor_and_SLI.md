---
title: "Gaming with Dual Monitor and SLI?"
date: 2009-08-04
forum: Gaming &amp; Leisure
---

### Post by keenish27 on 2009-08-04
I'm just curious if anyone does any gaming with Dual Monitors and SLI.  I've had some weird problems with this kind of setup and just wanted to know if anyone else experienced any weird problems with this setup.

---

### Post by gravity_blast on 2009-08-04
> **keenish27 said:**
> I'm just curious if anyone does any gaming with Dual Monitors and SLI.  I've had some weird problems with this kind of setup and just wanted to know if anyone else experienced any weird problems with this setup.

what kind of problems

---

### Post by Ericj1186 on 2009-08-04
Dual monitor AND SLi?  So, you are running 4 video cards or am I misunderstanding how this thing works?

Regardless, I had some really bad issues setting SLi up, so if you post the cards you have, I can tell you what I did.

---

### Post by keenish27 on 2009-08-04
> **gravity_blast said:**
> what kind of problems

Well at first to get x working i had to enter the pci bus for both my cards in the xorg.  After that everythign seemed to work fine but when I tried to play something in screen it maximizes across both screens.  Also when I tried to use something like Cedega or wine i couldn't change the resolution of the games, I was either stuck at 800x600 or I had to manually hunt through game config files and change them that way.

It just seems like it was way more hassle than it should be.

---

### Post by keenish27 on 2009-08-04
> **Ericj1186 said:**
> Dual monitor AND SLi?  So, you are running 4 video cards or am I misunderstanding how this thing works?

Regardless, I had some really bad issues setting SLi up, so if you post the cards you have, I can tell you what I did.

You are mis understanding a little bit.

I have 2 cards, and two monitors.  As of Januaryish nvidia's drivers let you do sli with dual monitors.

Anyway my I have 2 nvidia geforce 9800 gt's.

---

### Post by gravity_blast on 2009-08-04
sorry i have sh*tty ati so i have no idea

---

### Post by doomsayer97 on 2009-08-18
> **keenish27 said:**
> Well at first to get x working i had to enter the pci bus for both my cards in the xorg.  After that everythign seemed to work fine but when I tried to play something in screen it maximizes across both screens.  Also when I tried to use something like Cedega or wine i couldn't change the resolution of the games, I was either stuck at 800x600 or I had to manually hunt through game config files and change them that way.

It just seems like it was way more hassle than it should be.


Well, if you run games in Steam, here's what I did (for Left 4 Dead, which is why I have -novid)

```

-novid -height 900 -width 1440 -windowed
```Where '-height' is the height of your monitor, and '-width' is the width of it. So since my monitors are 1440x900, I would use those numbers for the corresponding places.
And I use -windowed because if a game opens in the middle of the two monitors, I can easily move it to one side :)

---


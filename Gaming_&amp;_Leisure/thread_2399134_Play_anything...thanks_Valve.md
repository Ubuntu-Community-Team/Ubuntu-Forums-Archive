---
title: "Play anything...thanks Valve"
date: 2018-08-22
forum: Gaming &amp; Leisure
---

### Post by MikeCyber on 2018-08-22
[https://www.gamingonlinux.com/articles/valve-officially-confirm-a-new-version-of-steam-play-which-includes-a-modified-version-of-wine.12400](https://www.gamingonlinux.com/articles/valve-officially-confirm-a-new-version-of-steam-play-which-includes-a-modified-version-of-wine.12400)

Cool but hopefully devs still target Linux natively.

---

### Post by oldrocker99 on 2018-08-22
I bought Bejeweled 2 Deluxe, which is on their currently limited list, and it ran perfectly. No futzing with wine, and this my be the start of a beautiful friendship!:)

However, Fallout Shelter crashed hard. Doki Doki Literature Club had such a shaky screen that it was unplayable.

It's early days. Give Steam a chance. One cannot say that they haven't supported Linux, and they have the firm intention to support us even more.

---

### Post by $yl9pAR%t on 2018-08-22
I have tested two games not listed by Steam so far.

Civilization IV Beyond The Sword - 60 fps and overall nice experience.
Railroad Tycoon 2 Platinum - only 10-20 fps but playable.

Edit:
After some more testing I can say I am happy with Company Of Heroes, Civ IV and Civ III. Almost happy (low fps) with Railroad Tycoon 2, but no luck with Age Of Empires II HD.

---

### Post by oldos2er on 2018-08-23
Downloading DOOM now. I know what I'm doing this weekend.

---

### Post by CharlesA on 2018-08-23
> **oldos2er said:**
> Downloading DOOM now. I know what I'm doing this weekend.

The new one? Please let me know what you think of it. I've been on the fence for quite a while.

---

### Post by oldrocker99 on 2018-08-24
> **oldos2er said:**
> Downloading DOOM now. I know what I'm doing this weekend.

Of course, due to my total suckage with FPS games (gimme a good RPG any day), I would no sooner play DOOM than hit my hand with a hammer:P.

---

### Post by oldos2er on 2018-08-25
> **CharlesA said:**
> The new one? Please let me know what you think of it. I've been on the fence for quite a while.

I had to update using the xorg-edgers PPA; using an Nvidia 1050ti with version 390.48, and it's running beautifully.

The gameplay in this version is more arcade style, i.e. quickly running and jumping around killing stuff, compared to the 2004 DOOM version. If you like that kind of thing I'd say go for it.

---

### Post by CharlesA on 2018-08-26
> **oldos2er said:**
> I had to update using the xorg-edgers PPA; using an Nvidia 1050ti with version 390.48, and it's running beautifully.

The gameplay in this version is more arcade style, i.e. quickly running and jumping around killing stuff, compared to the 2004 DOOM version. If you like that kind of thing I'd say go for it.

That sounds nice. I haven't finished the 2004 DOOM, but it's sitting in my backlog. Maybe I'll beat that one first. :)

---

### Post by pqwoerituytrueiwoq on 2018-08-26
> **oldos2er said:**
> I had to update using the xorg-edgers PPA; using an Nvidia 1050ti with version 390.48, and it's running beautifully.

The gameplay in this version is more arcade style, i.e. quickly running and jumping around killing stuff, compared to the 2004 DOOM version. If you like that kind of thing I'd say go for it.

You had to use the xorg edgers ppa to get 390.48, pretty sure that is available from the default sources
```
$ apt-cache policy nvidia-driver-390
nvidia-driver-390:
  Installed: (none)
  Candidate: 390.77-0ubuntu0~gpu18.04.1
  Version table:
     390.77-0ubuntu0~gpu18.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic/main amd64 Packages
     390.48-0ubuntu3 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/restricted amd64 Packages

```
thought i just installed the 396 driver (i upgraded to 1060 3gb the other week)
after a week of use my hdmi audio was acting strange (slow distorted playback), now it is working, well for now anyway
```
$ apt-cache policy nvidia-driver-396
nvidia-driver-396:
  Installed: 396.54-0ubuntu0~gpu18.04.1
  Candidate: 396.54-0ubuntu0~gpu18.04.1
  Version table:
 *** 396.54-0ubuntu0~gpu18.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by oldos2er on 2018-08-28
Haven't tried nvidia-396 yet, I guess I should do that soon. Thanks.

Edit: After double-checking I think it was the updated libvulkan* library from xorg-edgers that made the difference.

---

### Post by silverslimer on 2018-08-28
I've been trying this out since it was announced and got a lot of older Windows games to work BETTER than they did in Windows 10. Grand Theft Auto Vice City, Freedom Force and Dungeon Siege for example.

Of course, I also decided to try something more recent to give myself an idea of what to expect. Dishonored, from 2012, also ran beautifully.  

For Linux users who enjoy gaming, this is the greatest development in history.

---

### Post by caberry9 on 2018-08-29
anyone tested GTA SA?

---

### Post by $yl9pAR%t on 2018-08-29
[Steam Play Compatibility Reports by Community]("https://docs.google.com/spreadsheets/d/1DcZZQ4HL_Ol969UbXJmFG8TzOHNnHoj8Q1f8DIFe8-8/htmlview?sle=true#gid=0")

---


---
title: "Limbo and Ubuntu 13.10"
date: 2013-10-23
forum: Gaming &amp; Leisure
---

### Post by marco-7 on 2013-10-23
Hello,
I got Limbo with Humble Bundle and I installed it correctly on Ubuntu 13.04 using the .deb package provided.

When I upgraded to 13.10 the game was automatically uninstalled. I tried to reinstall it but it misses the dependency:

lib32asound2

I am running Ubuntu on a 64 bit system and ia32-libs seems correctly installed. Is there a way to install this package?

Thanks for the attention and regards,

Marco

---

### Post by ra-censhare on 2014-03-14
any movement on that topic yet?
Got my new pc yesterday and installed there ubuntu 13.10 of course  - and now, when I want to re-install my Limbo (Humble Bundle V, via Software Center) i get a "software not running with your ubuntu version" message in Software Center.
I checked and found that it is true, that if you look on the Software CEnter page for Limbo, ther eis 13.04 the most recent version - but WHY?
This game is so supdercool, and I bought it...
Does anyone know a workaround how to solve this?
To be honest it is way to much effort to run a VM with Ubuntu 13.04 on my machine only for the sake of playing this game - though I would love to!

Interesting side fact: on my old machine where I originally bought and installed Limbo under 13.04, it is still running after the update to 13.10 (at least I can access the game and see the start menu - checked that yesterday!)

---

### Post by spectatorx on 2014-03-14
Did you try in terminal:
> 

sudo apt-get -f install


to fix dependencies?

---

### Post by sffvba[e0rt on 2014-03-14
See post #4 here for a possible fix - [http://ubuntuforums.org/showthread.php?t=2181680](http://ubuntuforums.org/showthread.php?t=2181680)

---


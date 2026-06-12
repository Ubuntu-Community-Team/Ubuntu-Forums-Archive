---
title: "No 3d Acceleration when loading warsow on screen 1"
date: 2005-12-14
forum: Gaming &amp; Leisure
---

### Post by Cl1maX on 2005-12-14
Hi,

I am trying to run [www.warsow.net](www.warsow.net) version 0.7a on my machine on its own Xserver at display 1.

I have used the how to found at linux Gamers but to no avail.

My problem is that when I run warsow from a terminal in Gnome on my gnome display everything is fine as soon as i try a command similar to

sudo xinit $HOME/warsow/warsow $* -- :1

it loads a dispaly on screen 1 but without any 3d accelration so is running in software mode at abuot 1 FPS.

when i run it in the gnome screen (:0) it runs at 89 FPS at high resolution.

Has anyone got any ideas ?

My system is:

Breezy,
2800+ Semperon,
9700 Pro RAdeon (latest fglrx drivers from synaptic)
512 ram,

Many thanks in advance

---

### Post by Cl1maX on 2005-12-21
*** Bump *** 
I could really do with this working any help is massivly appreciated Cheers,

Cl1maX

---

### Post by kaamos on 2005-12-21
At least in the earlier versions of fglrx the acceleration worked only on screen 0. Try searching at atis site.

---

### Post by Cl1maX on 2005-12-22
[QUOTE=kaamos]At least in the earlier versions of fglrx the acceleration worked only on screen 0. Try searching at atis site.[/QUOTE]


Ahh really? :(  that kinda sucks.  

Cheers for the info, ill take a look :)

---


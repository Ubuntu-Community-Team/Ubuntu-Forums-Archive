---
title: "[Winex/Cegeda] Frozen Throne low performance !!"
date: 2005-04-10
forum: Gaming &amp; Leisure
---

### Post by VerrNum on 2005-04-10
Hi all,

i am using recent version of Cegeda to play to Frozen Throne.

My configuration is :

ATHLON XP 2100 XP
512 MO
Radeon 9800 PRO

i got recent ATI linux Driver

OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)

And  performance to fgl_gearx are ok :
2924 frames in 5.0 seconds = 584.800 FPS

But the game is slow..

I am OK that Winex emulation decreases performance of emulted games but, here the performances are slow...

The game is unplayable when there is too many units on screen.

I play in 1280x1204 @ 32 bits, but even if i decrease the resolution the game is not  faster !!?

Does i need to configurer something ???

Thanks to help me !!!

---

### Post by judyz on 2005-04-10
You may want to check the Cedega Wiki on this game.  It has several tips and fixes.  You can find it here.

[http://digital-conquest.ath.cx/wiki/index.php/Warcraft_III](http://digital-conquest.ath.cx/wiki/index.php/Warcraft_III)

---

### Post by gil-galad on 2005-04-10
[QUOTE=VerrNum]
2924 frames in 5.0 seconds = 584.800 FPS
[/QUOTE]

That is NOT ok.  You should be getting several thousand.  I am guessing 3d acceleration is NOT on.  It has nothing to do with emulating it.  Frozen Throne runs fine  with cedega.

---

### Post by digby on 2005-04-10
[QUOTE=gil-galad]That is NOT ok. You should be getting several thousand. I am guessing 3d acceleration is NOT on. It has nothing to do with emulating it. Frozen Throne runs fine with cedega.[/QUOTE]

This is definitely your problem.  Without 3d acceleration on, you'll get glxgears scores of ~500 fps.  My card (GF4 4600) get's well over 3k fps.  Check the howto section for info on installing the ati driver.

---

### Post by VerrNum on 2005-04-11
[QUOTE=gil-galad]That is NOT ok.  You should be getting several thousand.  I am guessing 3d acceleration is NOT on.  It has nothing to do with emulating it.  Frozen Throne runs fine  with cedega.[/QUOTE]

Hi,

Thanks for you answer..

Are you sure you didn't switch glxgears and fgl_glxgears...

My benchmark said : 

glxgears : 3217 FPS
fgl_glxgears : 584 FPS 

It's not OK ?!! :roll:

---

### Post by Dracontopes on 2005-04-11
[QUOTE=gil-galad]That is NOT ok. You should be getting several thousand. I am guessing 3d acceleration is NOT on. It has nothing to do with emulating it. Frozen Throne runs fine with cedega.[/QUOTE]

Actually, that score IS okay. He used **fgl_**glxgears, which shows a rotating cube with the gears inside.

---

### Post by gil-galad on 2005-04-11
[QUOTE=VerrNum]Hi,

Thanks for you answer..

Are you sure you didn't switch glxgears and fgl_glxgears...

My benchmark said : 

glxgears : 3217 FPS
fgl_glxgears : 584 FPS 

It's not OK ?!! :roll:[/QUOTE]

Yeah thats fine.  Sorry, I misread it.

---

### Post by jdodson on 2005-04-11
check this thread: [http://ubuntuforums.org/showthread.php?t=21970](http://ubuntuforums.org/showthread.php?t=21970)

try running some of those commands, it might help with performance.  you can also try vanilla wine from universe, it should be able to run war3 correctly with a no-cd crack.

---

### Post by VerrNum on 2005-04-18
[QUOTE=jdodson]check this thread: [http://ubuntuforums.org/showthread.php?t=21970](http://ubuntuforums.org/showthread.php?t=21970)

try running some of those commands, it might help with performance.  you can also try vanilla wine from universe, it should be able to run war3 correctly with a no-cd crack.[/QUOTE]

Hi all,


Thanks for your help,

the problem was the missing option : 

 "UseFastTLS" "2"


Thanks !!

---


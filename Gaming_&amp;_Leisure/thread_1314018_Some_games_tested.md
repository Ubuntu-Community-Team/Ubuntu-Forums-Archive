---
title: "Some games tested"
date: 2009-11-04
forum: Gaming &amp; Leisure
---

### Post by Diskdoc on 2009-11-04
I put a couple of hours on installing and testing some games available in Ubuntu (universe and multiverse enabled) but had some dissapointing results. Below I sum up the results for the games I tested. I am running 64-bit Karmic on a LG E300 laptop (Radeon Mobility x1250) with desktop effects enabled.

[LIST]
[*]Antigravitaattori: Start screen distorted, had to restore resolution manually after quit
[*]Openarena: Sound distorted, had to restore resolution manually after quit
[*]Frets on fire: Start screen text distorted 
[*]Gunroar: No way to start gameplay?
[*]KETM: No sound
[*]Noiz2sa: No way to start gameplay?
[*]Openglad: Distorted graphics
[*]Rrootage: No way to start gameplay?
[*]Sauerbraten: Had to restore resolution manually after quit
[*]Luola: No sound, crashed on exit
[*]Solarwolf: Had to restore resolution manually after quit
[*]Supertux2: Had to restore resolution manually after quit
[*]Teeworlds: Crashes when qutting, had to be killed from console, had to restore resolution manually
[*]Tremulous: No sound, crashed when trying to enable OpenAL (sound?). Had to be killed from console, had to restore resolution manually
[*]Pathogen: Distorted graphics
[*]Hedge wars: No sound, exiting game leaves black Hedgewars-window and hwengine eating cpu
[*]GL-117: Flickering from panel, had to restore resolution manually
[*]KQ: No sound, no fullscreen
[/LIST]

Often in 3D-games, flickering is present at the place of the system information-applet (as it draws the graphs). 

Games that worked ok: Torus Trooper, Tumiki fighters, Singularity, Slingshot, Dink smallwood, Ren'py (The question), The Bubs' Brothers, Waste's edge, Trigger.

To sum it all up..there seems to be a bit of a mess regarding sound and graphics support for games. Has anyone else noticed the same problems?

---

### Post by 5nak3 on 2009-11-04
try installing libsdl1.2debian-pulseaudio as opposed to the default libsdl1.2debian-alsa. This should sort out the teeworlds problem.

It may even fix some of the other games, but I really cant comment as I've not tried any of them.

If you want try out urban terror and warsow and see what happens on your end. Both these games refuse to play for me, either crashing right away or letting me play for a bit before crashing with no error report and in some cases even booting me back to GDM.

---

### Post by Diskdoc on 2009-11-04
I switched to libsdl1.2debian-pulseaudio and added the [Playdeb]("http://www.playdeb.net/") repository. Installed Teeworlds and Warsaw from there (newer versions). Teeworlds works properly now except for the very annoying screenflickering at certain spots I mentioned before (that I think is 3D/Compiz related). Looks like a fun game!

Tried Warsow too but it wouldn't start now, some error when trying to set fullscreen. Will report here when I/if I get around to try Urban Terror.

---

### Post by 5nak3 on 2009-11-04
Ok that's cool! 

Just to let you know (sorry if you already know this), it probably would be best to turn compiz off when playing as compiz does affect gaming for a lot of people.

Also a further request, if you could post the terminal output of warsow that would also be good as I can compare it to mine and maybe we may find a solution.

To do this simply run terminal and type warsow press enter and warsow should run and the terminal then records all the output...however in both our cases it will simply list the error we are having :)

---

### Post by Diskdoc on 2009-11-05
Here you go, the end of the terminal output. After that the game crashed and I had to restore resolution manually.


> ------------------------------------
Game running at 62 fps. Server transmit at 20 pps
Console initialized.

----- R_Init -----
Using libGL.so.1 for OpenGL...Display initialization
..XFree86-VidMode Extension Version 2.2
..XFree86-Xinerama Extension Version 1.1
..Got colorbits 24, depthbits 24, stencilbits 8
800x600 -> 1280x800: 200
800x600 -> 1280x720: 120
800x600 -> 1152x768: 168
800x600 -> 1024x768: 168
800x600 -> 800x600: 0
800x600 selected
...setting fullscreen mode 4:
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  129 (XFree86-VidModeExtension)
  Minor opcode of failed request:  17 (XF86VidModeGetGammaRamp)
  Value in failed request:  0x27
  Serial number of failed request:  63
  Current serial number in output stream:  63


---

### Post by 5nak3 on 2009-11-06
Yup, that's the exact same thing that I'm getting on the terminal crash. I've still not found a way to fix this except for booting up and playing in Windows.

To be fair while the solution may not be perfect it is a lot less of a hassle and I can actually play the game for two hours rather than trying to get the game to boot for two hours.

Next PC I'm getting an Nvidia card I think, this whole ATi support really has put me off their cards for a while.

---

### Post by Woojoo//.deb on 2009-11-06
it would be interesting to know which kind of grafics card you use ati or nvidia? and what type of drivers you use at the moment.

---

### Post by CharmyBee on 2009-11-06
> **Woojoo//.deb said:**
> it would be interesting to know which kind of grafics card you use ati or nvidia? and what type of drivers you use at the moment.

Radeon is an ATI chipset.

This is driver stuff, as bugs relating setting Gamma and Resolution were fixed some time ago, so do something about your drivers?

The x series are no longer supported by the latest fglrx, so you'll have to try the open source radeon driver. Don't know how well that'll work since I never tried that myself.

---

### Post by canningtony16 on 2009-11-21
I am also facing the same problem installing games.

---


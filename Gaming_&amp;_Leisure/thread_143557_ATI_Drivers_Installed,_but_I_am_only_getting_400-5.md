---
title: "ATI Drivers Installed, but I am only getting 400-500 FPS in fgl-glxgears."
date: 2006-03-12
forum: Gaming &amp; Leisure
---

### Post by Dakaru on 2006-03-12
Im only getting 400-500, when I hear people getting around 3,000. (Games Play fine though), Is it normal to get 400-500 or is there a way to get more?

---

### Post by Horndog on 2006-03-12
what is your output of this:

```
fglrxinfo
```

---

### Post by Dakaru on 2006-03-12
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X700 Generic
OpenGL version string: 2.0.5695 (8.23.7)

---

### Post by Horndog on 2006-03-12
That looks like the correct driver is installed. What test did you use (there are two) also a list of relevant hardware would help.

---

### Post by Dakaru on 2006-03-12
I ran

fgl-glxgears.

My PC is.

AMD Athlon 64 3200+
ATI Radeon x700
1gb DDR 3200 RAM
160GB HD
Ubuntu Linux Running Fluxbox.


But I played PlanetPenguin-Racer and it is smooth as glass. As is Armegetatron. UT04, Plays double speed.. So are they working?

---

### Post by Horndog on 2006-03-12
[QUOTE=Dakaru]I ran

fgl-glxgears.

My PC is.

AMD Athlon 64 3200+
ATI Radeon x700
1gb DDR 3200 RAM
160GB HD
Ubuntu Linux Running Fluxbox.


But I played PlanetPenguin-Racer and it is smooth as glass. As is Armegetatron.[color=red] UT04, Plays double speed..[/color] So are they working?[/QUOTE]
[QUOTE=tseliot]Another test: play an mp3 in Totem (or another app). If it goes too fast then you have this problem[/QUOTE]
Check this page out:
[http://ubuntuforums.org/showthread.php?t=75281]("http://ubuntuforums.org/showthread.php?t=75281")

---

### Post by Dakaru on 2006-03-12
Everything plays at normal speed accept for UT04, and UT04 has been known to, there is a scipt to make it normal but I don't know how to use it.

---

### Post by Horndog on 2006-03-12
[QUOTE=Dakaru]Everything plays at normal speed accept for UT04, and UT04 has been known to, [color=red]there is a scipt to make it normal[/color] but I don't know how to use it.[/QUOTE]

Could you post a link to the script please. If you think your system is not "double clocking" then please post the output of:


```
fgl_glxgears

```
and
```
glxgears -printfps

```

---

### Post by Dakaru on 2006-03-12
20331 frames in 5.0 seconds = 4066.050 FPS

That is for glxgears-printfps

And my friend sent me the script via msn.

---


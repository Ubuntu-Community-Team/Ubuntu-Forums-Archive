---
title: "Counter Strike 1.6 launch in opengl"
date: 2007-07-24
forum: Gaming &amp; Leisure
---

### Post by ARTO^UK on 2007-07-24
I launch Cs with wine using this line ```
env WINEPREFIX="/home/joe/.wine" wine "C:\Valve\Steam\steam.exe" -applaunch 10 -width 1280 -height 800 -Opengl
```
but it will not launch in OpenGL mode. Once in game I can change to opengl but this is rather annoying every time I start up.

I've also tried -gl but that didn't work either. Anyone got a solution? :-k

---

### Post by ubuntu.daemon on 2007-07-24
i dont think it would work with the capitalized O??  oh b4 you throw on those options, just try
```
user@home:~$  wine steam.exe -opengl
```
and shouldn't it be 1280x960??

but anyways cd in xterm to your steam directory and try above coding....

---

### Post by ARTO^UK on 2007-07-24
That doesn't work. And its 1280x800 because I'm on a widescreen display, I am adding the parameters correctly because the resolution does change.. Anymore ideas?

---

### Post by Motoxrdude on 2007-07-24
> **ARTO^UK said:**
> I launch Cs with wine using this line ```
env WINEPREFIX="/home/joe/.wine" wine "C:\Valve\Steam\steam.exe" -applaunch 10 -width 1280 -height 800 -opengl
```
but it will not launch in OpenGL mode. Once in game I can change to opengl but this is rather annoying every time I start up.

I've also tried -gl but that didn't work either. Anyone got a solution? :-k

```
env WINEPREFIX="/home/joe/.wine" wine "C:\Valve\Steam\steam.exe" -applaunch 10 -width 1280 -height 800 -opengl
```
Try that.

---

### Post by ARTO^UK on 2007-07-24
I can't see a difference there.. Anyway I tried it and it didn't work. :?

---

### Post by aidanr on 2007-07-24
i think it's just -gl not -opengl

edit:// oh sorry, i see you already tried that

---

### Post by ARTO^UK on 2007-07-24
Yeah I tried that but it still didn't work :(

---

### Post by Motoxrdude on 2007-07-25
> **ARTO^UK said:**
> I can't see a difference there.. Anyway I tried it and it didn't work. :?

Instead of -Opengl i did -opengl.

How is annoying on startup with opengl?

---

### Post by ARTO^UK on 2007-07-25
Pardon?

Does this actually work for anyone?

---

### Post by ARTO^UK on 2007-07-26
*bump*

---

### Post by eiskalt on 2007-07-26
when you open counterstrike, do you have the option to set a resolution?  Can you change it between opengl or d3d or softwarE?  If you dont have those options, odds are something was out of wack when you compiled wine.

---


---
title: "[SOLVED] Driver supporting 3D hardware acceleration"
date: 2007-06-18
forum: Gaming &amp; Leisure
---

### Post by farueulogy on 2007-06-18
I've been looking at some of the games at [www.getdeb.net](www.getdeb.net) and they're interesting.

The majority of their 3D games include the warning:
"This game requires a driver supporting 3D hardware acceleration."

As there was no information if I had this or how to obtain such I decided to simply install a game called assultcube and see if it'll get by. It installed fine but once in game everything is really slow and I assume this is because I don't have the driver.

Does anyone know what I have to install?

I'm running Ubuntu 7.04 on a dell insipron 9300 laptop and I've been able to run 3d games happily on my windows partition (eg Rome: Total War).

---

### Post by farueulogy on 2007-06-18
I've taken a look at [https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html](https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html)

I've gone to the terminal and ran:

> glxinfo | grep rendering


to see if my 3D acceleration was working and suprisingly it was:

> $ glxinfo | grep rendering
direct rendering: **Yes**


Anyone have any ideas as to why the game is running so poorly?

---

### Post by cogadh on 2007-06-18
What video chipset does that laptop have (ATI, nVidia, Intel, etc.)? 

By default, 3D accelerated drivers are not installed in Ubuntu. After determining what type of video hardware you have, you will need to install the drivers yourself. There are numerous "how-to" posts on this subject here and in the "Multimedia and Video" forums.

EDIT - well you type just as fast as me apparently. You should still identify your video hardware so we can assist with troubleshooting it.

---

### Post by tgm4883 on 2007-06-18
What video card do you have?

Do this in terminal and post the output.

```
glxinfo | grep direct
```

---

### Post by johnny4north on 2007-06-18
he has - nVidia GeForce 6800 Go :)    Go here > panel > System > administration > restricted drivers.  click > enable > close, reboot and you are done.

---

### Post by cogadh on 2007-06-18
Um, how do you know? The Inspiron 9300 had a variety of available hardware, including the ATI Radeon X300, GeForce 6xxx GO and Intel 915 integrated.

---

### Post by tgm4883 on 2007-06-18
> **johnny4north said:**
> he has - nVidia GeForce 6800 Go :)    Go here > panel > System > administration > restricted drivers.  click > enable > close, reboot and you are done.

I'm wondering how this would help since he already has direct rendering enabled.

---

### Post by cogadh on 2007-06-18
> **tgm4883 said:**
> I'm wondering how this would help since he already has direct rendering enabled.
Yeah, that confused me a little too.:?:

---

### Post by hikaricore on 2007-06-18
> **cogadh said:**
> Yeah, that confused me a little too.:?:

If I'm not mistaken (which believe it or not has happened before) the NV driver supports direct rendering...but badly.

Just my 2 cents. Take it as you will.

---

### Post by Cappy on 2007-06-18
Yes, what he actually needs to post is
```

glxinfo | grep OpenGL
```
It shows what drivers are in use.

---

### Post by farueulogy on 2007-06-19
> **johnny4north said:**
> he has - nVidia GeForce 6800 Go :)    Go here > panel > System > administration > restricted drivers.  click > enable > close, reboot and you are done.

Maybe this isn't good practice, but it worked! Huah!

---

### Post by cogadh on 2007-06-19
Glad to hear it! Just goes to show you, every once in a while a random stab in the dark will work! :)

---

### Post by tgm4883 on 2007-06-19
> **cogadh said:**
> Glad to hear it! Just goes to show you, every once in a while a random stab in the dark will work! :)

It's not so much a random stab in the dark.  We all thought it was the 3D drivers.  And following the instructions posted would have loaded the drivers for the card whether it was an nVidia card or an ATI card

---

### Post by bitumen on 2007-06-26
lol this also worked for me to hahahahaha radeon x300se
1st post on these forums 
1st time on a non windows personal system ( been using windows since msdos days)
Linux will be home now ( im loving it )

---


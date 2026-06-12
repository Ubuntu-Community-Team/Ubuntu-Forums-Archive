---
title: "WoW video mode problems"
date: 2007-04-01
forum: Gaming &amp; Leisure
---

### Post by Myos on 2007-04-01
I've been playing WoW on my pc for about a year now and I decided to switch over to Linux today thinking that I could continue playing, but I am having some problems.

I have Wine and WoW installed.  When I run Wow.exe - d3d it loads up and displays the intro movie.  Once I hit enter to skip past it Wow closes and I get dumped back to the desktop.  If i run Wow.exe -opengl my computer just straight up freezes.

I've been trying to find the appropriate driver for my videocard but I can't seem to figure out what to get or how to install it.  Right now I am just using "Intel Corporation 82915G/GV/910GL Integrated Graphics Controller" which is more than enough to run the game.

Any ideas before I'm forced to go back to Windows?

---

### Post by lakersforce on 2007-04-01
Have you tried the guide on the Ubuntu Wiki:

```
https://help.ubuntu.com/community/WorldofWarcraft
```

I think the intel chipset is already supported. Have you done a:

```
$ glxinfo | grep rendering
direct rendering: Yes
```

---

### Post by hikaricore on 2007-04-01
The intel drvers are missing many important functions for the card to work properly on most systems.  Get an nvidia card and save yourself the hassle.

---

### Post by leetcharmer on 2008-02-25
I also have the same problem on Intel Graphics.  The movie plays at the beginning and then WoW just stops.  No errors, or anything.  Just closes.  Not sure where to begin.  I haven't been able to find any results on this issue with google.

---

### Post by Perfect Storm on 2008-02-25
Closed due to necromancing.
Please check our wine forum for Window Games.


[img]http://www.imageviper.com/displayimage/82451/0/1114981414_fullres.jpg[/img]

---


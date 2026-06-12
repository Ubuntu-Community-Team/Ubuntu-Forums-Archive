---
title: "Savage 2 &quot;OpenGL 2.1 not available&quot;"
date: 2008-11-28
forum: Gaming &amp; Leisure
---

### Post by Nevon on 2008-11-28
I just installed Savage 2, but now I can't get it to start. If I start it in the terminal I get this error message:
```
Savage2 - Fatal Error: OpenGL 2.1 not available.
Savage2 - Fatal Error: Segmentation Fault

Segmentation fault
```
And here's the output of lspci:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```

My graphics card is a Intel GMA intergrated X4500HD.

Anyone know if there's a way to fix it?

---

### Post by eragon100 on 2008-11-28
> **Nevon said:**
> I just installed Savage 2, but now I can't get it to start. If I start it in the terminal I get this error message:
```
Savage2 - Fatal Error: OpenGL 2.1 not available.
Savage2 - Fatal Error: Segmentation Fault

Segmentation fault
```
And here's the output of lspci:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```

My graphics card is a Intel GMA intergrated X4500HD.

Anyone know if there's a way to fix it?

It can't be fixed, sorry :(

Intel's open-source drivers don't support opengl 2, only up to 1.5.

The power of free software! :rolleyes:

(Nvidia and ATI closed drivers already support opengl 3.0)

---

### Post by Nevon on 2008-11-28
> **eragon100 said:**
> It can't be fixed, sorry :(

Intel's open-source drivers don't support opengl 2, only up to 1.5.

The power of free software! :rolleyes:

(Nvidia and ATI closed drivers already support opengl 3.0)

Oh man. That sucks! What about closed source drivers, are they available at all? Are they any better?

---

### Post by Riven213 on 2008-12-23
damn... I was just about to post the same topic.

> Oh man. That sucks! What about closed source drivers, are they available at all? Are they any better?

anyone?

---

### Post by spoons on 2008-12-23
Intel don't do closed-source drivers. I thought that the drivers did OpenGL 2 by now, but obviously not. You're gonna have to wait, sorry.

---

### Post by eragon100 on 2008-12-23
Like I said, the power of free software!

This is why I prefer closed-source video drivers :wink:

OpenGL 2.1 has been around since 2005 (or 2006), and intel still doesn't support it. They are still at 1.5, while 3.0 is out now (which closed nvidia drivers already support, 3.0)

---

### Post by Riven213 on 2008-12-23
:/

omg, that sucks.
I didnt know OpenGL 2.1 was so old. Why don't they do anything about it?
it's a serious letdown.

is there a website dedicated to these open source drivers?
I only found [http://intellinuxgraphics.org/index.html](http://intellinuxgraphics.org/index.html) but there is no 'news' section and nothing mentioned about an upgrade...

---

### Post by mikedep333 on 2008-12-23
There is some luck on the phoronix forums.

[http://www.phoronix.com/forums/showthread.php?t=13139](http://www.phoronix.com/forums/showthread.php?t=13139)

---

### Post by Vadi on 2008-12-23
Ouch. I just looked up your card - it seems it's comparable to my 8600M GT. It can tank s2 on medium-high settings.

---

### Post by eragon100 on 2008-12-24
> **Vadi said:**
> Ouch. I just looked up your card - it seems it's comparable to my 8600M GT. It can tank s2 on medium-high settings.

WHAT? An IGP 4500 HD is comparable to a GeForce 8 8600 GT non-integrated??
Are you sure?
source?

---

### Post by Vadi on 2008-12-24
Hey, to my unexperienced eye the specs looked similar.

---

### Post by Nevon on 2008-12-24
> **eragon100 said:**
> WHAT? An IGP 4500 HD is comparable to a GeForce 8 8600 GT non-integrated??
Are you sure?
source?

I don't have any sources or any data to support it, but just out of my own experiences I can say that it's a pretty darn good card if you have the drivers to properly back it up. I can run Savage 2 on medium-high without any noticeable drop in frame rate, and I can run stuff like Mount & Blade, Day of Defeat, The Sims 2, and a lot of other games without any major problems. 

But that doesn't really matter when the Linux drivers suck. :(

---

### Post by Extreme Coder on 2008-12-25
With Fedora, Intel cards support GL 2 fine. Blame Ubuntu for using an older libdrm :P

---

### Post by Vadi on 2008-12-25
You mean latest Fedora version out less than a month ago?

Bet you couldn't say that two months ago then, when I was already playing S2 for half a year ;)

---

### Post by biji on 2008-12-27
hmmmm.... just downloaded savage but won't run
./modelviewer.sh 
Savage2 - Fatal Error: OpenGL 2.1 not available.
Savage2 - Fatal Error: Segmentation Fault

Segmentation fault

and also Unigine_Sanctuary ..... both needs opengl 2 :(

---

### Post by mad_max0204 on 2009-02-03
Anyone had this issue on Nvidia 9800GT 1gb ??
Savage2 - Fatal Error: OpenGL 2.1 not available.

I installed latest nvidia drivers manually.
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT (rev a2)

Thanks


EDIT: I installed 180.27 beta drivers. Now when I rolled back to 180.22 it works.

---

### Post by Vadi on 2009-02-03
Known issue with 180.27 - they report "OpenGL 3.0" heh. See this thread: [http://forums.savage2.com/showthread.php?t=15652](http://forums.savage2.com/showthread.php?t=15652)

---

### Post by biji on 2009-04-08
using jaunty.... still savage won't run............. :(
using intel x3100

---

### Post by Vadi on 2009-04-09
> **biji said:**
> using jaunty.... still savage won't run............. :(
using intel x3100

Yeah it won't, the intel drivers for linux don't have support for opengl 2.1 :\

(don't worry, there are lots of mac users too who can't run the game too. too weak graphics cards, the fancy plastic casing doesn't cut it)

---

### Post by rizzeh on 2009-04-09
> **mad_max0204 said:**
> Anyone had this issue on Nvidia 9800GT 1gb ??
Savage2 - Fatal Error: OpenGL 2.1 not available.


 I fixed this by launching Savage 2 dedicated server and running update from server console, update has fix for this bug with 180.xx drivers and Savage 2 not recognising OpenGL 3.0

---

### Post by linuxguru1 on 2009-04-26
I'm using 9.04 Jaunty too and I'm running with the official NVidia drivers (180.29)... I get the "OpenGL 2.1 not available" error aswell... is it fixable?

> # glxinfo | grep "OpenGL version"
OpenGL version string: 3.0.0 NVIDIA 180.29


---

### Post by Perfect Storm on 2009-04-26
Run the ./savage2_server.bin and/or ./savage2_update.bin first.

---

### Post by Vadi on 2009-04-26
Just need to run the server (dedicated_server.sh) for a bit 'till it updates the game and then you'll be good to go.

Issue was an outdated library was detecting opengl 3.0 wrong, they're working on an updated installer.

---

### Post by Pasdar on 2009-04-26
Hey, you get what you paid for. Intel cards are the worst on the market.

---

### Post by CharmyBee on 2009-04-26
> **Pasdar said:**
> Hey, you get what you paid for. Intel cards are the worst on the market.

Too bad it's not even a card (intel hasn't done 3d cards since i740), and it's an integrated **mobile** chipset. Doesn't leave you with much for upgrade choices, so there's no use pulling a 'too bad should have got a gf9800 sli'

---

### Post by linuxguru1 on 2009-04-28
> **Artificial Intelligence said:**
> Run the ./savage2_server.bin and/or ./savage2_update.bin first.


Thanks... that helped me out :)

---

### Post by maheshjr2000 on 2009-04-28
What I dont get is that Mesa 7.4.1 DOES support opengl 2.1. Can someone tell me how to upgrade to it?

---

### Post by Firestem4 on 2009-04-28
edit: read post wrong

---

### Post by maheshjr2000 on 2009-04-28
edit, he edited XD.

---

### Post by Artemis3 on 2009-07-10
> **Artificial Intelligence said:**
> Run the ./savage2_server.bin and/or ./savage2_update.bin first.

savage2_update.bin also complains: "Savage2 - Fatal Error: OpenGL 2.1 not available." With 9800gt.. So i just started the server, and see what it does.

---


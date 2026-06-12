---
title: "AssaultCube doesn render fonts! Please help."
date: 2008-04-04
forum: Gaming &amp; Leisure
---

### Post by SandmanXC on 2008-04-04
I have the AssaultCube from GetDeb.com . When running it all none of the fonts actually appear. Instead of them, just colored blocks. I installed libsdl-ttf, and still nothing. Any help please?

PS: Everything else seems to run fine, just no fonts what-so-ever.

---

### Post by SandmanXC on 2008-04-04
bump

---

### Post by plinydogg on 2008-04-05
Same problem here. The website says this:

Linux users: Make sure you have libSDL 1.2, libSDL_image and libSDL_mixer  installed.

I've got libSDL 1.2, but there is no option in Synaptic to get libSDL_image or libSDL_mixer...

Any help would be much appreciated!

---

### Post by plinydogg on 2008-04-05
Looks like there's no solution on the official forums either:

[http://assault.cubers.net/forum/comments.php?DiscussionID=513&page=1](http://assault.cubers.net/forum/comments.php?DiscussionID=513&page=1)

---

### Post by plinydogg on 2008-04-05
It would be great if someone could post some screenshots of the menus...

All I'm trying to do is make it so that I can play a single player game. As it is now, the game is in multiplayer mode by default and there's no one to fight!

---

### Post by Surreal Killa on 2008-04-06
I'm having the same issue. White rectangles instead of text.

---

### Post by plinydogg on 2008-04-07
Is this a graphics card issue? I've got an ATI 200M Express (not the greatest). What do you have?

---

### Post by Rhubarb on 2008-04-07
It's best to download assault cube from assault cube's website (rather than off getdeb)
[http://assault.cubers.net/download.html](http://assault.cubers.net/download.html)
As the getdeb download introduces problems when getting new maps for the game.

32bit installation guide:
[http://gaming.gwos.org/doku.php/guides:32bit:assultcube](http://gaming.gwos.org/doku.php/guides:32bit:assultcube)

64bit installation guide:
[http://gaming.gwos.org/doku.php/guides:64bit:assultcube](http://gaming.gwos.org/doku.php/guides:64bit:assultcube)

I have no problems running assault cube here on my system (core2duo, nVidia 7950 512MB, 4GB RAM, Ubuntu 7.10 64bit)

---

### Post by SandmanXC on 2008-04-07
I believe the issue is re;ated to the ATI graphics cards drivers. I've requested some help with this [here]("http://ubuntuforums.org/showthread.php?t=745955").

---

### Post by Surreal Killa on 2008-04-19
I figured out the problem. Instead of having the default ATI driver (xorg-driver-fglrx) you need the official one from ATI. Easy to install using Envy. And if the game 'flickers' you need to turn off extra effects in compiz.

---

### Post by plinydogg on 2008-04-19
Sorry for my total ignorance, but what is Envy?

---


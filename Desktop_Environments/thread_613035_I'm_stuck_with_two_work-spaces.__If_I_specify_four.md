---
title: "I'm stuck with two work-spaces.  If I specify four, it stays at two."
date: 2007-11-14
forum: Desktop Environments
---

### Post by diablo75 on 2007-11-14
I've just re-enabled compiz to see if my video card will make it crash (I have an nvidia 5500 OC, and I think the fact that it's overclocked causes it some problems and an eventuall crash, but we'll see...it's a different story anyway).

So, I have two workspaces by default, basicly giving me a 2 sided "cube" to flip around, when I want four sides to give me an actual cube.  When I click on the work space boxes in the lower right hand corner, and choose properties, I'll enter 4 (or any number).  And then hit ok.  The number of boxes in the work-space selector stays the same, and I still have a two sided wall that I can flip around..

:confused:

---

### Post by l2thet on 2007-11-14
Gah I cant give you exact details as to why this is happening, but the core of the problem, is your increasing virual desktops.  I had that problem as well, but im not at my linux box, so I can give you a set of defined instructions, until I get home.  

You need the extra compiz package, i think it was

gnome-compiz-manager,

after thats intalled you will have more options under preferences,
then you go to general options in that option(pretty lame huh?)
inside there you can extend how many actual desktops you have, when you set that to 4 you will have a cube,

When I get home I will post the real deal, but I cant atm.

---

### Post by ayoli on 2007-11-14
Go to menu system > preferences > advanced desktop settings
if you don't have it type this in a terminal to install it :
```
sudo apt-get install ccsm
```
once in advanced desktop settings, choose "general", then pick "desktop size" tab and set virtual horizontal size to 4.

---

### Post by l2thet on 2007-11-14
yeah what he said... 
all the stuff I was thinking, my stuff was pretty off lol

---

### Post by diablo75 on 2007-11-14
Well, compiz crashed on me as expect so I'm not going to worry about this.  Though, after loging off and back on , then disabling compiz, I now have four workspaces available to me...and the properties windows where this setting is changed looks a little different.

No biggie.  I'm going to get myself a better video card someday...

---

### Post by oneadvent on 2007-11-14
No, you cant give up because I know the solution to this, in ccsm, it is under general option, then one of those tabs there specify the number of desktops, put the top number as 4 and the rest as 1.


Ok, I kinda knew the answer...that should get you close anyway.

---


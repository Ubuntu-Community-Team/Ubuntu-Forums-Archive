---
title: "Use Xorg instead of xgl?"
date: 2007-10-05
forum: Desktop Effects &amp; Customization
---

### Post by 7llusion on 2007-10-05
I was told that i could get xorg to be used instead of xgl, how is this possible, since I installed my compiz with a script that also installed xgl, but unfortenately xorg works slowly on my computer...
Please help

---

### Post by Rupertronco on 2007-10-05
Your post is incredibly confusing but I'm guessing it's XGL that's slow, not regular X right?

What are your system specs, especially your graphics card?

---

### Post by 7llusion on 2007-10-05
I have a intel i810 card and it's xgl thats really slow it uses about 38% of the CPU most of the time...

---

### Post by eentonig on 2007-10-05
Running Compiz? That's rather normal I guess. The i810 isn't that much of a high end graphics card.

---

### Post by Jouke74 on 2007-10-05
Your Intel can indeed handle AIGlX on the X-server (xorg) instead of the XGL server. Just remove the scripts that you made and start-up with a normal session instead of a XGL session. Then click on enable desktop effects in the menu and xorg.conf should be edited to run AIGLX.

---

### Post by 7llusion on 2007-10-05
No, I mean that I used a .sh to install compiz so I wouldn't have to go through all the compiling business([http://forum.ubuntu-fr.org/viewtopic.php?pid=1011875](http://forum.ubuntu-fr.org/viewtopic.php?pid=1011875)) and it seems to have made xgl my default.
I'm wondering how to put back xorg.

---

### Post by Rupertronco on 2007-10-06
Change the session when you log on to just Gnome instead of Gnome + XGL. Don't use scripts to install things like Compiz, because if something goes wrong you won't be able to identify what step went wrong and why. 

You need to completely remove XGL, it's useless for Intel cards, you can use AiGLX as said before.

Scripts may be easier, but now you're stuck because you used a script (probably for an ati card) to save a few extra minutes, and it's not saving you any time now.

---

### Post by Jouke74 on 2007-10-06
That's the hard way of telling it... plus most scripts usually don't backup stuff.

---


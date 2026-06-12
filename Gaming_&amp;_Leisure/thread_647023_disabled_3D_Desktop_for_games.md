---
title: "disabled 3D Desktop for games"
date: 2007-12-21
forum: Gaming &amp; Leisure
---

### Post by Dark Aspect on 2007-12-21
Is it possible to run a game or application inside a 3D desktop but make it where the program does not use the 3D effect?Star Wars KOTOR does not like my 3D desktop but I was not wanting to disable 3D.Is there a work around or do I have to disable my 3D effect every time I play the game and re-enable it afterwards?

---

### Post by cogadh on 2007-12-21
Sorry, you're going to have to disable/re-enable every time you play a game. Especially a game played through Wine. In fact, the Wine FAQ specifically mentions this:

> Using composite display managers in Linux tends to cripple OpenGL performance or break OpenGL entirely which is why we recommend that you disable them and remove composite from XOrg entirely before trying to use Wine. If you are using one and experiencing slow performance then DO NOT FILE BUGS as this is not a Wine bug. Just because TuxRacer runs fine doesn't mean it is Wine's fault, Windows games normally require a little more umph than basic Linux native games. Also to make sure, run glxinfo and make sure that it says "Direct Rendering : Yes".

---

### Post by Dark Aspect on 2007-12-21
ok well thanks anyway,odd that wine says it breaks OpenGL entirely some games don't mind my 3D desktop on wine just a few.I guess this applies to crossover too,I normally don't play games though crossover but Halo works that way.

---

### Post by chronusdark on 2007-12-23
i made shortcuts 

CTRL + SHIFT + F5 = metacity --replace &
CTRL + SHIFT + F6 = compiz --replace &

you can set these up in advanced desktop effect settings
that way its easy to switch them off and on

im hoping that someone will come up with a plugin or something for compiz that will detect another app using openGL and switch automatically (thats what vista does)

---

### Post by Tyke91 on 2007-12-23
how did you set this shortcut?

---

### Post by chronusdark on 2008-01-22
you have to install the advanced desktop effects applet

i cant remember the package name right now but goto the general settings area in that applet and you can set them up there

---


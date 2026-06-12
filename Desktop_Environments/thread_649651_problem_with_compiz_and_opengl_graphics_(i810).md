---
title: "problem with compiz and opengl graphics (i810)"
date: 2007-12-25
forum: Desktop Environments
---

### Post by radovid on 2007-12-25
Hi,

I have a weird problem with the opengl rendered images while running compiz on my computer.

Actually everything seems to work fine until I try to run an windowed opengl application.
It doesn't matter if the program is glxgears, amarok visualisation plugin or google earth. In any of these cases the opengl image prevails over all other windows and it remains on the top of any window which is in foreground. 

For example (as you can see from the attatched screenshot) if I run glxgears and try to put in front of the runing gears a window of a console, the console window covers the border of the glxgears window, but not the running gears and it is shadowed by them. (you can imagine how it could be annoying with the drop down menues in celestia).

There is another issue, which I belive it is connected. The opnegl rendered animation detaches itself while rotating the desktop cube. So it does not reamin on the desktop, but follows you while rotating the cube, as you can see on the second screenshot. It disapears when you enter another desktop.

I belive thet I've mised some settings in connection with the opengl video output and/or compiz.


If I turn of compiz everything works fine...

I use an intel 855GM graphic card.

Can somebody help me?

---

### Post by Triggerhapp on 2008-02-17
Sorry to bump up a rather old post.

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
```

Im having the same troubles.
I figured it out after weeks of trying to get xwinwrap to work, it always seemed to throw the screen saver over the top of every other window.
I'll be honest, I have no idea how to fix it...

Other artifacts I can describe are that the polygons on "CubeGears" Plugin do not seem to be ordering themselves (nearest ones SHOULD show up, not the furthest ones) and, as said before, opengl images detach from the desktop when using cube rotate.

Any one think they have a clue? XD
Thanks ahead. - Trigg

---

### Post by Triggerhapp on 2008-04-18
bump.

---

### Post by jsh-hk on 2008-07-03
bump

---

### Post by deNoobius on 2008-07-03
What driver are you using for your graphics card?  Go to System/Administration/Hardware drivers, and make sure the "enabled" box for your driver is checked.

---


---
title: "Beryl and Compiz Fusion Errors, How to Fix?"
date: 2007-07-10
forum: Desktop Effects &amp; Customization
---

### Post by DeadSuperHero on 2007-07-10
Hey all, I need some advice.
I've reinstalled Ubuntu on my old computer, to give to a friend in need. I'm trying to get some eye-candy working (beryl, AWN, screenlets) and it seemed to be working fine at first.
Then I decided to install compiz fusion, to show him how slick it is. Unfortunately, this screwed everything up. He now needs to use the terminal to start up emerald and Compiz Fusion, and although it somewhat works, we get a problem with Emerald and window borders. They're simply not there, and you can't move the windows. I know for sure that this isn't drivers with the gfx card, as 3D rendering is working fine.
So, what is it then? Why is it acting like this, and how can I fix it so that my friend can have just one or the other?
Help me out?

---

### Post by macogw on 2007-07-10
Does the cube work at all? No borders and windows can't move (you tried alt +click & drag, right?) sounds like the WM crashed (especially if they're all in top left...are they?).  Any errors when he runs it from the terminal?

---

### Post by DeadSuperHero on 2007-07-10
We're not able to manipulate the cube at all, or any of the eyecandies. Or even move the windows.
We can still access them and work inside of them, but we can't move them anywhere on the screen.

---

### Post by macogw on 2007-07-10
Do any errors print out in the terminal when he launches beryl?

---

### Post by DeadSuperHero on 2007-07-10
Here's the output: 
> **************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

[Warning ]: Relaunching beryl with __GL_YIELD="NOTHING"

**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Segmentation fault (core dumped)
zac@Axiom:~$ 



And when we do that, the window borders disappear, and we can't access anything.

---

### Post by DeadSuperHero on 2007-07-11
Figured I'd bump again. Could the errors be caused by Compiz Fusion and Beryl working against each other?

---


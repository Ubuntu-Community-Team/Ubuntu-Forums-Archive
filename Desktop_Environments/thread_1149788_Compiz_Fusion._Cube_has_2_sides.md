---
title: "Compiz Fusion. Cube has 2 sides ?"
date: 2009-05-05
forum: Desktop Environments
---

### Post by DeusExM1 on 2009-05-05
I have installed the compiz fusion app. I enabled the cube and "rotate" the cube options. I can rotate the desktop but for some reason it only has 2 sides. So i cant see a cube at all. Its basically just "flipping" the desktop.

Its like having a piece of paper in front of your face and rotating it in any way you want.

Why does my cube not work?

---

### Post by aesis05401 on 2009-05-05
Try System/Preferences/CompizConfig Settings Manager.

Then click on 'General Options,' and navigate to the final tab, "Desktop Size."

Try Horizontal Virtual Size=4, Vertical Virtual Size=1, Number of Desktops=4.

---

### Post by DeusExM1 on 2009-05-05
Thanks a lot !!! This is exactly what i wanted :)

---

### Post by evanrmurphy on 2009-05-05
Or you can leave Number of Desktops = 1, with the other settings as aesis05401 described. There's a difference between having one desktop with four viewports and four desktops with one viewport each, though the distinction is a bit slippery. See the [Compiz Wiki]("http://wiki.opencompositing.org/GeneralOptions#Desktop_Size") and [this thread]("http://forum.compiz-fusion.org/showthread.php?t=5325") for more about it.

To tell the truth, I recently settled on the two-sided "cube". Can we call it the *Compiz Sheet*? ;)

---

### Post by DeusExM1 on 2009-05-05
Thats some good advice. I have modified my settings accordingly.

The only question i had left is: I have the cube set up now, and skydome enabled. But how do i put an image on top and bottom of the cube? Is there a way to change it from a single color?

---

### Post by evanrmurphy on 2009-05-05
In the same *CompizConfig Settings Manager*, go to *Desktop Cube* under the *Desktop* category, and click on the *Appearance* tab. Here you can change the *Cube Color*, or add an image under *Cube Caps* to be displayed instead. I think the default image given there is /usr/share/gdm/themes/Human/ubuntu.png (which may not even exist), but if you replace that with the image of your choice, or add and move it to the top of the list, it should have display priority.

Now, by some quirk of Compiz, I think as such your image will only be shown on the top cap. If you want to see it on the bottom too, you need to go back to the *CompizConfig Settings Manager*, and find *Cube Reflection and Deformation* under the *Effects* category. Here, under *Appearance* in the *Cube caps* tab, you can control the color and/or image of each cap individually (meaning you could even use a different image for the top and bottom, if you wanted to). Once you check the box to enable *Cube Reflection and Deformation*, these cube cap settings should override the ones under *Desktop Cube*.

Hope this helps!

---

### Post by DeusExM1 on 2009-05-05
Thanks a lot !  I have no configured it perfectly how  i wanted it :) Cheers.

---

### Post by UKBB on 2009-06-05
> **aesis05401 said:**
> Try System/Preferences/CompizConfig Settings Manager.

Then click on 'General Options,' and navigate to the final tab, "Desktop Size."

Try Horizontal Virtual Size=4, Vertical Virtual Size=1, Number of Desktops=4.

I go there but I don't have a tab labeled "Desktop Size.

Never mind, I got it. Thanks!

---

### Post by UbuntuNerd on 2009-06-05
> **UKBB said:**
> I go there but I don't have a tab labeled "Desktop Size.

Never mind, I got it. Thanks!

you can also do the same thing by looking at the bottom right of your desktop(your work spaces)right click on it and select preferences and select 4 columns 1 row.

---

### Post by UKBB on 2009-06-05
It looks like I have some memory issues. With a program open on 3 of the 4 desktops everything shuts down, even the AWN Toolbar. There is only 512meg on this old Dell P4 machine. I've also noticed that I can't rotate with the mouse if a window is maximised.

---

### Post by ActionParsnip on 2010-07-29
If you make a script to run at startup that contains:


#!/bin/bash
sleep 10
avant-window-navigator &


Then it will make AWN wait before running, this gives all the compiz fluff time to load and can help.

---


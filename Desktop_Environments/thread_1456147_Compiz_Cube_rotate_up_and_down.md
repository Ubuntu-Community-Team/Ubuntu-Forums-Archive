---
title: "Compiz Cube rotate up and down?"
date: 2010-04-16
forum: Desktop Environments
---

### Post by srilyk on 2010-04-16
Hi, I've recently enabled the fun stuff with compiz but I've run into a sort of problem... I want 9 desktops in a 3x3 grid (yeah, weird I know) but if I'm using the cube I can only rotate left and right... which is pretty weak sauce. Is there any way to (preferred) have desktops on the top and bottom of the cube and be able to bind a key combo to rotate up and down (ctrl-alt-up/down)? I *could* put 9 desktops in a row, but I really don't like that solution - it takes too many flips to make it from one desktop to another.

Any help will be greatly appreciated! Compiz is all full of beautiful (especially burning the windows on close)
:guitar:
Thanks,
Wayne

---

### Post by QIII on 2010-04-16
The cube only rotates around a vertical axis.  There is a good reason for this.  And it's not weak sauce.

If you have a 16:9 aspect ratio on your screen, you can rotate through a series of 16:9 faces horizontally.

The top and bottom faces of your cube are going to be 16:16, which would not fit on your screen.

What if you have 5 workspaces?  You get a pentagon 16 on a side.  6 workspaces?  A hexagon 16 on a side.

The fact is that when the "cube" happens to have 4 workspaces, it is not a proper cube (a "regular hexahedron" with six square surfaces), but a cuboid (a hexahedron with three pairs of rectangles as its surfaces.  In this case, one pair (the top and bottom) are squares.)

9 workspaces wouldn't work on a cube anyway, since there are only 6 surfaces on a hexahedron.

Make your "cube" a cylinder.  Set control-alt-left click to rotate the cube.  That will allow you to drag the cube around.  If you keep moving your mouse, you can drag the cube all the way around to the original workspace and beyond. I you have a long desk, you can spin it around several times.

---

### Post by srilyk on 2010-04-18
That's a bummer. I tried out 9 desktops wide and it feels... well, wide :P

I prefer rows and columns because then I can order my windows with better relations - my browser on one desktop, stuff I'm programming to the right, a paper I'm working on below... and so on and so forth.

What I really want is something that has my rows on the left to right, but when I go up and down instead of say the cube caps, it's another row.

Basically something that works just like the wall switcher but in 3d.

If there's anything like that already, that would be super cool... sadly I'm sure there isn't. Any clue on how difficult it is to program compiz plugins?

---

### Post by triva911 on 2010-08-04
How I can add a workspace to up and down in cube ... when i rotate i se up and down a yelow empty workspace ... ???

---

### Post by mcduck on 2010-08-04
> **triva911 said:**
> How I can add a workspace to up and down in cube ... when i rotate i se up and down a yelow empty workspace ... ???

You can't. It's explained in the very first answer to this thread. Top and bottom of the cube aren't correct shape to be used as desktops.

---

### Post by deanmac5 on 2010-09-30
I have tried this in Kubuntu and KDE based Mint (10.10 beta and 9 respectively) and it works fine. You can rotate the cube vertically and horizontally. However it doesn't seem to work in Gnome in Ubuntu (10.04 or 10.10 beta).
I guess if you're really keen on it you can switch to KDE.

---

### Post by sikander3786 on 2010-09-30
> **deanmac5 said:**
> I have tried this in Kubuntu and KDE based Mint (10.10 beta and 9 respectively) and it works fine. You can rotate the cube vertically and horizontally. However it doesn't seem to work in Gnome in Ubuntu (10.04 or 10.10 beta).
I guess if you're really keen on it you can switch to KDE.
How did you accomplish that on Kubuntu and Mint? Was it enabled by default?

Please post a link to the guide you followed to accomplish this so others can benefit ;-)

---

### Post by terobin on 2011-01-19
I've got a dual monitor system set up, so my resolution is effectively 3040x900. I was hoping to have four workspace stacked on top of each other, and have the cube rotate along a horizontal axis instead of a vertical one. Is this possible?

---

### Post by rg4w on 2011-01-29
Bummer.  I was hoping to do the same thing with a vertical orientation.  It would seem just a matter of flipping the cube on its side; that is, if such an option existed.  Oh well...

---

### Post by heyandy889 on 2011-02-02
As for the desktops not fitting because the top of the cube is the wrong size, well, is the world of geometry, yes. There can't be a physical object constructed to look like that. However, this is a virtual desktop. A handful of people in this thread are already imagining it. Since it's virtual, we're not bound to the restrictions of physical space.

For example, I use LauncherPro for Android on my Droid X. It has a "desktop cube" feature for flipping between homescreens. Anytime you flip to the left or right, LauncherPro displays a 90-degree turn from desktop to desktop. It even lets you set the number of homescreens to >4. Where Compiz compensates for this and makes a hexagonal prism, LauncherPro simply ignores the fact that flipping an item through itself is a physical contradiction. So, it might lead to some cool software if we mix our physical rules with the possibilities of a virtual desktop.

---


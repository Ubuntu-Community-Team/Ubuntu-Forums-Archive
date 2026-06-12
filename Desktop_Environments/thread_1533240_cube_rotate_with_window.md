---
title: "cube rotate with window??"
date: 2010-07-17
forum: Desktop Environments
---

### Post by soryu on 2010-07-17
im trying to rotate the cube by dragging the windows.
like when you have desktop wall enabled.but it's not working i've been messing around with rotate cube settings to no avail.
i can rotate the cube,just not with windows.
all other settings work
flip edge,flip with window edge.

anyone got a solution?
thank's

---

### Post by mgmiller on 2010-07-17
I assume you are trying to get your cube to rotate when you drag a window to the right or left edge.

There is a setting buried in ccsm somewhere for that, but I find the easiest is to install simple-ccsm.  This will add a new very simple gui for controlling many compiz functions.

```
sudo apt-get install simple-ccsm
```

Once it's installed, run it from System > Preferences > Simple Compizconfig Settings Manager.

Go to the last tab to the right "Edges".

On the graphic of the screen, click on the right edge and select  "Rotate Cube: rotate flip right"

On the left edge, do the same thing but select "Rotate Cube: rotate flip left.

The edges in the graphic will change from red to green to show the change.

That's it.  Try dragging a window to the right or left edge of the screen and it should flip the cube around.

Have fun  :popcorn:

---

### Post by soryu on 2010-07-18
thanks that worked,but when the mouse is over the edges the cube rotates.
just want it to rotate with the window only. i think i have some thing else enabled???
ill have to keep at it.

---

### Post by stinkeye on 2010-07-19
ccsm > desktop > rotate cube
There are three edge flip settings...
**edge flip move** is the one you want.

---

### Post by soryu on 2010-07-19
thanks, also had to set rotate flip left and right corners in bindings to get it working.:KS

HEYNow!

---

### Post by mgmiller on 2010-07-19
To turn off the cube rotate when the pointer hits the edge, in CCSM  go to Rotate Cube.  The first choice at the top to the list is "edge flip pointer", you want to uncheck that.  That should do it.

---


---
title: "resizing windows from the command line"
date: 2009-01-08
forum: Desktop Environments
---

### Post by Ace_NoOne on 2009-01-08
Unfortunately, I cannot run Compiz when using an external monitor ([Compiz-Check]("http://forlong.blogage.de/entries/pages/Compiz-Check") reports that my 3200x1200 resolution is too high, as the graphics chip's max. 3D texture size is 2048x2048).
This means I can't use Compiz's Tile plugin.

So I'm wondering whether there is a way to move and resize windows from the command line (e.g. using Python) - that way I could write a script to run on startup, setting default dimensions for common applications.

---

### Post by zhocchao on 2009-01-08
hi
you can use wmctrl to resize and place windows. (I wrote a bash-tiling-script for metacity. If you want i'll send you this.)
g
z

---

### Post by Ace_NoOne on 2009-01-09
> **zhocchao said:**
> you can use wmctrl to resize and place windows. (I wrote a bash-tiling-script for metacity. If you want i'll send you this.)
*wmctrl* looks very promising!
It might take me a while to get used to it - so your Bash script would definitely be helpful. Could you add an attachment to this thread?

---

### Post by zhocchao on 2009-01-09
the tiling script places the active window on the left side in the biggest window. Values are hard coded, so they have to be changed. my resolution is 1024x800. It's for 1-9 windows
i don't use min/max so the function is commented (to slow).
the other script places the active window smaller on the side.
Comments are in german but not to hard to understand.
I would be interested to have the scripts as a extra-window-managing-script in python. (If you or someone else...)
I hope this helps for your first steps
g
z

(My first post was better but somehow it got lost)

---

### Post by Ace_NoOne on 2009-01-14
Thanks for sharing, zhocchao!

Unfortunately, I haven't been able to test this yet, as I'm having [technical problems]("http://ubuntuforums.org/showthread.php?t=1028636") (thus my late response).
Will report back as soon as my situation has normalized.

---

### Post by Ace_NoOne on 2009-01-19
I've had some time to look at your scripts - and while they did get me started on the *wmctrl* basics (essentially, *wmctrl -r <windowTitle>  -e "0,-1,-1,<width>,<height>"*), I'm having trouble understanding the scripts per se.

I've thought about creating a generalized script in Python, but currently don't really see much value in that, as I basically only have on standard window arrangement (i.e. hardcoded values). Automated tiling turns out to be not very helpful in my case, as it essentially means treating all windows equally.

Again, thanks for your help!

---

### Post by zhocchao on 2009-01-19
I'm glad it helps you i some way.

Just as an answer and in case someone drops by:
I thought about 
- different possibilities to arrange windows.
- a gui to define a pattern on the screen
- rules for windows, in which window they should place
- automatic tiling as an option (tried it, but i don't like it)
- the possibility to minimize a window on desktop to a reasonable size (with rules)

It would be a bigger project, than just making one script out of two.

g
z

---

### Post by corentin.barbu on 2010-04-07
Hi,
I've downloaded and changed the script. 
- I've fixed one bug : some windows id made the program to bug.
- I've made the tiling to affect only active windows.
- I began to centralize the change of size value using the screen definition. You have to change the screen definition manually in the beginning of the script. I only centralized up to 3 windows as I never use more tiled windows on one desktop.
- the "main" window use 2/3 of the width of the screen (this should be centralized in later versions if any).

Hope it can be of use.

CBC

---

### Post by Atilana on 2010-04-07
the tiling script places the active window on the left side in the  biggest window. Values are hard coded, so they have to be changed. my  resolution is 1024x800. It's for 1-9 windows

---

### Post by corentin.barbu on 2010-04-07
Hi all,
Here is a new version of the tiling script. It allows automated tilling allowing the width of the "active"  window to remain the same and other windows to adapt to it. I found the script much more efficient and handy this way. You can change the main windows size and launch the script, other windows automatically adapt.

To adapt tiling to "active" windows size : 
tileprio.sh 1

To use default width of main windows :
tileprio

Attilana : with this script adapted from yours, values are no more hard coded for the cases with 1 to 4 windows. You only have to change the screen definition to let it work even if small modifications can be needed.  

Hope it could be of use. 

CBC

---

### Post by zlatkart on 2010-04-07
@corentin.barbu

I wrote a version of this script in C. It is faster with extra functionality (but maybe a bit harder to customize). However you're idea is very interesting and  I'll implement this in the next version

---

### Post by proc on 2010-04-25
@zlatkart

I would be interested in trying your script... what about releasing it?

---

### Post by zlatkart on 2010-04-25
...can be found here:

[http://gtk-apps.org/content/show.php/ctrlwm?content=114565](http://gtk-apps.org/content/show.php/ctrlwm?content=114565)

---


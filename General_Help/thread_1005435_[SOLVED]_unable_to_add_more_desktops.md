---
title: "[SOLVED] unable to add more desktops"
date: 2008-12-08
forum: General Help
---

### Post by zivxx on 2008-12-08
hey guys, ive installed the required compiz fusion items for the cube, but i cannot add me desktops, so i figured out my graphic card was blacklisted, and i ignored it by writing
```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```
and then i entered ```
ccsm
```
and it opened the compiz manager, so i checked all the cube stuff and when i clicked on general effects, i went to the desktop tabs but i have no option to add more desktops...
any ideas?

---

### Post by eternalnewbee on 2008-12-08
Is this what you're looking for?

---

### Post by pastalavista on 2008-12-08
or you can right click on the workspaces panel (or add it to a panel if you don't already have it) and select 'preferences' and change the 'columns' entry to however many workspaces you want. I have four but I have increased the 'columns' to 20 once and had a 20 sided polygon for a 'cube'. I don't know if changing the 'rows' setting affects the cube or not...

---

### Post by Kevbert on 2008-12-08
What graphics card do you have ? and what version of Ubuntu ?

---

### Post by zivxx on 2008-12-08
Pastalavista, im not sure what are you talking about
Kevbert, again im not sure but i think its intel chipest family <number i can't remember> 3100x and i have ubuntu 8.10

---

### Post by zivxx on 2008-12-08
Pastalavista, im not sure what are you talking about
Kevbert, again im not sure but i think its intel chipest family <number i can't remember> 3100x and i have ubuntu 8.10

---

### Post by pastalavista on 2008-12-08
@zivxx- lower right corner boxes is what I'm talking about
[ATTACH]95669[/ATTACH]

---

### Post by zivxx on 2008-12-08
well buddy, i tried adding to 4 and to 20, but none of them give me cube i get some kind of a circle =(

---

### Post by pastalavista on 2008-12-08
ah...what you want is in the 'effects' section. 'Cube reflection and deformation'...on the deformation tab select none

[ATTACH]95673[/ATTACH]

---

### Post by skippymo on 2008-12-08
you might have added to many, a 20 sided object might look like a circle...

my cube has four sides.

---

### Post by zivxx on 2008-12-08
well, mine is checking and my whole window looks like that:
[http://img389.imageshack.us/my.php?image=adsfjd2.jpg](http://img389.imageshack.us/my.php?image=adsfjd2.jpg)
well, not the whole window but the important parts of it

---

### Post by pastalavista on 2008-12-08
click on 'cube reflection and deformation' and you should see this screen after you click the 'deformation' tab [ATTACH]95678[/ATTACH]> **zivxx said:**
> well buddy...=(
happy now? your attitude made me sorry I tried to help at all

---

### Post by Kevbert on 2008-12-08
What you need to do is to go to Preferences-CompizConfig Settings Manager-General Options, under desktop size set Horizontal Virtual Size to 4, then press back. Make sure Desktop Cube is ticked. Make sure Rotate Cube is ticked and set Zoom under the general tab to 0.6, then press back. Make sure Deformation and Reflection are not selected (for now). Close Compiz Manager.
Now if you click on another desktop workspace (bottom righthand corner of the screen) you'll see the cube rotate.  Another way to rotate the cube is to hold down Ctrl-Alt and press the left or right arrow, or with Ctrl-Alt held down, click and hold the lefthand mouse button and move the mouse around.

---


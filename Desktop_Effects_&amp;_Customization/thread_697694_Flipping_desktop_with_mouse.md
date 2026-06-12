---
title: "Flipping desktop with mouse"
date: 2008-02-15
forum: Desktop Effects &amp; Customization
---

### Post by KillerHurdz on 2008-02-15
Hi, I was wondering if there was a way to switch desktops (with the Cube) without having to go to the taskbar or having to actually move a window to the next "side".  For example either being able to move the cursor to the left or right hand side of the screen or using the side buttons on the mouse.

Is this possible?

---

### Post by ronmarley1 on 2008-02-15
In CCSM, go to the Rotate Cube plugin.  Tick the box next to "Edge Flip Pointer" and that will rotate the cube when you move the mouse pointer to the edge of the screen.  On the Actions tab of the same plugin, you can map keys or mouse buttons to do various actions.

---

### Post by KillerHurdz on 2008-02-15
Hey thx for the help.  I have one question though... I am totally new to Ubuntu (2 days new) and don't have the slightest clue on how to get that plugin.  I know it's probably really simple but I'm a hardcore Windows user and I'm still learning Linux.

---

### Post by PinkFloyd102489 on 2008-02-15
Open up a terminal and enter this:

```

sudo apt-get install compizconfig-settings-manager

```

---

### Post by KillerHurdz on 2008-02-15
> **PinkFloyd102489 said:**
> Open up a terminal and enter this:

```

sudo apt-get install compizconfig-settings-manager

```

Thanks.  Ive made progress.  Now it says:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: Couldn't find package compizconfig-settings-manager**

---

### Post by PinkFloyd102489 on 2008-02-15
You need to enable all repositories.

System -> Administration -> Software Sources

Enable universe and multiverse.

---

### Post by nilarimogard on 2008-02-16
Try: ctrl + alt + left click somewhere and drag the mouse, that should drag the cube.

---

### Post by ronmarley1 on 2008-02-17
Change your repositories as Pink Floyd wrote above then install CCSM.  You can run it from a terminal by typing ```
ccsm
``` is a terminal window.
Furlong's blog has a ton of info. on configuring Compiz.  Here's the link: [http://forlong.blogage.de/article/2007/10/2/Desktop-effects-by-default-in-Gutsy---how-Compiz-Fusion-enhances-Ubuntus-desktop-of-version-710](http://forlong.blogage.de/article/2007/10/2/Desktop-effects-by-default-in-Gutsy---how-Compiz-Fusion-enhances-Ubuntus-desktop-of-version-710)

---

### Post by notwen on 2008-02-17
I typically use ALT+CTRL+(LEFT or RIGHT)  while alos having the scroll wheel option available on the desktop.  I use expo on my laptop, so my keyboard shortcuts are a bit easier.

---

### Post by chavanak on 2008-02-17
I also use the ALT+CTRL+ LEFT or RIGHT. For expo, i have mapped it to the top left corner. So when i want to see all my desktops i take my pointer to the top left corner!!

---

### Post by nilarimogard on 2008-02-18
To see 3 desktops, you can also press CTRL + ALT + down arrow and then left or right

---


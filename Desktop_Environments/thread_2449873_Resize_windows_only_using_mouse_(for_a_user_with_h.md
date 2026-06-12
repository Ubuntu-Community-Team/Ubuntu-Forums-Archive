---
title: "Resize windows only using mouse (for a user with handycap)"
date: 2020-09-03
forum: Desktop Environments
---

### Post by robbystarck on 2020-09-03
Hi,

i know that resizing windows on xfce is a big problem and i know that i can do this with ALT and right click. But this isn't helpful for my because i lost my right hand 2 years ago and i can't use keyboard and mouse at the same time. Is there any way to resize windows only with mouse? I use greybird and here the area at the window edge where i can resize the window is sooo small. Can i change this by do some changed in one of the themes files? Or mapping right and left mouse button at the same time to the combination of ALT+right click? Can i change this behaviour with an other theme? If so it should possible to change greybird.

robby

---

### Post by &amp;KyT$0P# on 2020-09-03
I use Openbox window manager instead of xfwm4 and select an Openbox theme with thicker window borders.

Also, for what it's worth, last I checked in xfwm4 it might be easier to resize window from the top corners.

---

### Post by CatKiller on 2020-09-03
You might find that [sticky keys](https://docs.xfce.org/xfce/xfce4-settings/accessibility) would do the trick for you.

---

### Post by robbystarck on 2020-09-03
can be helpful will try it.

using openbox is not a solution. there are reasons why i use xfce. i  also tried kwin with xfce but i will never again install any kde stuff.

is this small "resize area" a problem with the window manager or the theme? what process manages how thin this area is?

---

### Post by &amp;KyT$0P# on 2020-09-03
> **robbystarck said:**
> using openbox is not a solution. there are reasons why i use xfce. 

To be clear, I did **not** suggest ever switching away from Xfce.  It's possible to use openbox under Xfce, that's what I'm doing right now and on multiple machines.

> is this small "resize area" a problem with the window manager or the theme?

I think it's the theme.  Try the Breeze xfwm4 theme? -
```
sudo apt-get install xfwm4-theme-breeze
```

---

### Post by tea for one on 2020-09-04
When you open a window in XFCE, there should be a little icon on the top left generally above File.

Left click will open a little menu with a **Resize** option.

The resize control will appear at the bottom right corner of the open window.

Move the mouse and click again when you are happy with the resized window.

[ATTACH=CONFIG]286878[/ATTACH]

---


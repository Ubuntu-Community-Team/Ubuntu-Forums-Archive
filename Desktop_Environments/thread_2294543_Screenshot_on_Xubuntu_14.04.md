---
title: "Screenshot on Xubuntu 14.04"
date: 2015-09-11
forum: Desktop Environments
---

### Post by eightbits2010 on 2015-09-11
I recently installed Xubuntu 14.04.03 along side a Ubuntu 14.xx  install.

Everything seems to operate as expected but I do have an issue
with using 'screenshot' and selecting the &#8220;select a region' option. On a Ubuntu install  
that section works fine but on the Xubuntu 14.04.3 this blackens the screen

making it extremely difficult to see where to start the region to capture.
After using the mouse to start the selection , then that area  will show  the actual
screen area as the mouse (right button held down) moves to complete the capture.
I have no idea what if anything I can do to get screenshot to work  on Xubuntu the same
as the Ubuntu OS. I am hoping I can get some help on this as I like to us the screenshot  
frequently.

---

### Post by CantankRus on 2015-09-13
If you don't need compositing turn it off in 
settings > window manager tweaks

I have an xfce4 session installed in regular ubuntu and when using gnome-screenshot 
in my xfce4 session the whole screen doesn't go dark.
So if you want compositing, try **gnome-screenshot**.
Simulate (-s) installing first and if you're happy with the extra packages it may pull in, remove the "**-s**" from the command...
```
sudo apt-get **-s** install gnome-screenshot
```

Personally I use **shutter** to take screenshots because you can use a timer and has editing plugins.

---

### Post by Dennis N on 2015-09-14
I suggest you take the screenshot of the entire screen, then crop the image in gimp so you can later precisely select the area to be captured. You also then get the time delay option active so you can also capture menus. In fact, I don't see a good reason to even use the "select a region" option.

---


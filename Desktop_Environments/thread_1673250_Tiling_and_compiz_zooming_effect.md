---
title: "Tiling and compiz zooming effect"
date: 2011-01-22
forum: Desktop Environments
---

### Post by byte1918 on 2011-01-22
I'm pretty new to ubuntu/linux and my knowledge about window managers is limited, so please bare with me. I was wondering if anyone knows a decent wm that supports tiling and can also have the zoom effect from compiz (mod+scroll up/mod+scroll down). I know compiz can achieve some tiling with the grid addon but that's not that great. I was looking for something more similar to how xmonad manages windows and workplaces. 

Thanks

---

### Post by Pogeymanz on 2011-01-22
I'm not sure how it is, but Compiz does have a tiling plugin. As in REAL tiling. Google that and see if that suits you.

---

### Post by stinkeye on 2011-01-22
Using a combination of easystroke (mouse gestures) or your own keyboard shortcuts, and wmctrl to control the size and placement of windows to your own liking is fairly easy.


From man wmctrl
> <MVARG> 
A move and resize argument has the format 'g,x,y,w,h'. All five components are integers. The first value, g, is the gravity of the window, with 0 being the most common value (the default value for the window). Please see the EWMH specification for other values. 
The four remaining values are a standard geometry specification: x,y is the position of the top left corner of the window, and w,h is the width and height of the window, with the exception that the value of -1 in any position is interpreted to mean that the current geometry value should not be modified.

eg I use this to resize and centre a window for my screen size.
```
wmctrl -r :ACTIVE: -e 0,400,200,875,550
```

---

### Post by byte1918 on 2011-01-22
> **stinkeye said:**
> Using a combination of easystroke (mouse gestures) or your own keyboard shortcuts, and wmctrl to control the size and placement of windows to your own liking is fairly easy.


From man wmctrl


eg I use this to resize and centre a window for my screen size.
```
wmctrl -r :ACTIVE: -e 0,400,200,875,550
```

This seems interesting, I'll look into it, thanks.

---


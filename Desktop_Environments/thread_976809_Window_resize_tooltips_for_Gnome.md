---
title: "Window resize tooltips for Gnome"
date: 2008-11-09
forum: Desktop Environments
---

### Post by Andrew_P on 2008-11-09
I'm missing a way to display a tooltip during window resizing, when the corner of the window is being dragged with the mouse.  This is a commonly-available feature in X Windows environments on Unix, but I haven't found a way to activate it, if it exists at all, in Ubuntu.:frown:  There is a freeware utility for Microsoft Windows, called Sizer, that works nicely with Windows 98SE and later; it displays the window size in x-pixels and y-pixels while dragging, and by right-clicking on the window corner, pops up a context menu that allows one to resize the window to several user-defined presets, such as 640x480, 800x600, etc.  This comes in very handy during Web page development and GUI programming, allowing one to test the behavior of the program on various display sizes.  Does something similar exist for the Gnome desktop?

---

### Post by hictio on 2008-11-09
If I understood correctly, and you want to see the size of the window you are resizing as you do it, and you are running Compiz, make sure to enable the plugin "Resize Info", that on Intrepid's compizConfig Setting Manager its located on the "Utility" category.

---

### Post by Andrew_P on 2008-11-09
Thanks for the information.  I installed CompizConfig Settings Manager, and now when I go into System -> Preferences -> Advanced Desktop Effects Settings, I found where I can check the box labeled Resize Info, under Utility.  Unfortunately, I can't get it to work.:(  It apparently only works with Desktop Effects enabled, and whenever I try to enable it on my machine, I see the message "Desktop effects could not be enabled."

My current Ubuntu machine is an off-brand Intel Celeron 2.4 GHz laptop with 15-inch XGA display, and the video channel is apparently unable to support Desktop Effects.  I'll need to wait until I can try Ubuntu on a more capable desktop machine.:mad:

---

### Post by Andrew_P on 2009-01-23
> **Andrew_P said:**
>  I'll need to wait until I can try Ubuntu on a more capable desktop machine.:mad:

I now have that machine, equipped with an NVIDIA GeForce 5500 video card, 256MB of video RAM and running Ubuntu 8.10.  Advanced Desktop Effects Settings work and I can see the window dimensions when I drag the edges or corners.:)  It's a bit finicky to use, though, not nearly as quick and easy as Sizer in MS Windows, and there's apparently no way to store several custom window sizes so one can instantly run a web browser at, say, 640x480 to see how a Web page would look on a standard VGA display.  The Gnome Desktop implementation of Resize Info *looks* impressive, but uses waaay too much CPU power and memory for what it needs to do.  This should have been made to work even without Advanced Desktop Effects.

---


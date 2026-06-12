---
title: "Compiz - Maximized window has annoying small top margin"
date: 2019-09-01
forum: Desktop Environments
---

### Post by nathanfranke on 2019-09-01
I've continually had an issue with my home Xubuntu installation, and now I am getting the same issue with Ubuntu MATE. For both installations, Compiz is installed.

AskUbuntu Post: [https://askubuntu.com/questions/1123076/compiz-cannot-easily-drag-window-from-top](https://askubuntu.com/questions/1123076/compiz-cannot-easily-drag-window-from-top)
XFCE Forum Post: [https://forum.xfce.org/viewtopic.php?pid=54015#p54015](https://forum.xfce.org/viewtopic.php?pid=54015#p54015)
Reddit Post: [https://www.reddit.com/r/Ubuntu/comments/ctatjs/xubuntu_1804_compiz_cannot_drag_from_top_of/](https://www.reddit.com/r/Ubuntu/comments/ctatjs/xubuntu_1804_compiz_cannot_drag_from_top_of/)

Basically, all of my windows have a ~2px top margin that prevent me from dragging it from there. It isn't much of an issue with unmaximized windows because I have to click more precisely anyways. However, on maximized windows, I typically drag my mouse all of the way to the top of the screen and then hold to drag it.

[https://media.giphy.com/media/ggLJs4HDoQ9RH7PTjs/giphy.gif](https://media.giphy.com/media/ggLJs4HDoQ9RH7PTjs/giphy.gif)

---

### Post by CatKiller on 2019-09-01
The way the screen edge plugins work is to detect the cursor entering the 2 pixel area at the edge of the screen. This behaviour can mess up other applications. For me it was the Rotate Cube plugin and the side edges messing up some games that didn't expect the screen edges to be restricted.

The options as I see them are [list] [*] Move the cursor 2 pixels down before you click. You're already doing this and I can see that it would be really annoying. 
[*] Disable whichever plugin is triggered by the top screen edge. It might turn out to be something that you never use, or it might be something that you use all the time; I have no idea. 
[*] Have your panel at the top rather than the bottom. You may find this behaviour more acceptable for panel items where you already have to aim rather than the title bar where you should be able to just throw the mouse to the edges. If you use the panel more than you move screens around it could be even more annoying. 
[*] Hold the Alt key while dragging anywhere else in the window to pull the window away from the top edge. 
[/list]

---


---
title: "How to make Unity workspaces disconnected ?"
date: 2011-06-09
forum: Desktop Environments
---

### Post by ilkerk on 2011-06-09
Hi all,

I'm working on 3-4 workspaces and each has several windows. After switching to a workspace I usually find the corners (or sides) of the windows hanging from other workspaces. Then I need to bring the all the windows (that I'm going to work) to front by clicking or by alt-tab.

Is there a way to prevent a window to "hang over" (not sure if that is the correct verb) other workspaces ? I know this is the point of dragging windows from one workspace to another but I prefer to do this by using expo.   

thanks.

---

### Post by Copper Bezel on 2011-06-09
Unfortunately, no, Compiz doesn't have an option for this, just as the 2D window manager, Metacity, doesn't have an option *not* to work that way.

---

### Post by ilkerk on 2011-06-09
metacity may be what I'm looking for. is it comparable to unity, and is there a way to switch and test metacity ? 

thanks.

---

### Post by Copper Bezel on 2011-06-09
Well, Unity is a Compiz plugin, but there is a package unity-2d in the repositories that can run under Metacity. You can switch to Metacity simply by running metacity --replace, but your Unity panels will disappear.

Metacity really isn't comparable to Compiz in the sense that it doesn't really offer any visual effects, and by default, it doesn't even use compositing for transparent parts of windows (although this setting can be changed.) It's used in conjunction with the Clutter compositor in Gnome Shell.

---

### Post by ilkerk on 2011-06-09
Thanks for the replies, 
after trying both (and messing up)  I decided to go back Unity and live with it. May be in future there may be an option for this. 

thanks again.

---


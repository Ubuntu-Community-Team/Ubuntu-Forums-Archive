---
title: "Can not resize window and other issues"
date: 2012-01-12
forum: Desktop Environments
---

### Post by jpaulb on 2012-01-12
After my old box I built in 2004 died, I bought my first brands name, Dell XPS 8300 with Windoze 7 installed. I decide to down load Wubi and try out the different flavors of Ubuntu, as I am not overlycjoyed with the new Ubuntu desktop.

I installed Kbuntu for a try and then Xububtu. after a couple of days Xubuntu started to act up. I lost the ability to resize windows, switch desktops, move windows. The only way to close a window is to goto file and click on quit.

I installed Xubuntu permanently a couple of days ago and today the same issues occurred.

Is there a fix for this short of reinstalling?:confused:

---

### Post by LewisTM on 2012-01-12
I think the solution is in this [thread]("http://ubuntuforums.org/showthread.php?t=1811712").

Also you should delete the hidden ~/.cache/session file which might be contaminated by faulty session settings. 

It is a sporadic bug of the XFCE Window Manager, xfwm4. If you get it repeatedly you might want to try another Window Manager. You machine should handle Compiz fine and it provides nice 3D effects. Install fusion-icon to get a permanent panel icon through which you can restart or switch your window manager on demand, handy when your display is giving you trouble.

Cheers!

---

### Post by jpaulb on 2012-01-12
Thanks
removing ~/.cache/session solved it.

---


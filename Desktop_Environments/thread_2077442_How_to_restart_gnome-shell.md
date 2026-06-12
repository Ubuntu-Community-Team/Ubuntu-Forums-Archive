---
title: "How to restart gnome-shell?"
date: 2012-10-28
forum: Desktop Environments
---

### Post by Drone4four on 2012-10-28
After killing a process, what is the bash syntax to indicate a follow up command?  I tried &#8216;kill 3171 && gnome-shell&#8217; for example, but that doesn&#8217;t work.  

I am trying to kill and restart my gnome-shell...If I kill the gnome-shell id with top, then all my open windows revert to my first workspace...I want to maintain my 43 windows organized in their respective workspaces as I restart my gnome shell.  Gnome 3.0 did this automatically...like I could just kill the gnome-shell process id and it would restart automatically and all the windows would still be in the correct workspace...but starting in Gnome 3.2, if my memory serves me correctly, I&#8217;d lose all my boarders around the windows and I would have to use a virtual terminal to kill the X server and then I would have to start up all my applications again...The same is true for Gnome 3.4.1 which I am running on 64bit Ubuntu 12.04 right now.

I Googled &#8216;restart gnome shell&#8217; and I found a really useful &#8216;cheat sheet&#8217; which says that you can restart the Gnome window manager by initiating ALT + F2 and then typing either &#8216;r&#8217; or &#8216;restart&#8217;... This is sort of what I am looking for, but upon trying it out, while it does kill gnome-shell, upon restart it crashed.  I lost all my workspaces and I couldn&#8217;t ALT + TAB to a console to type gnome-shell to start it up again.  I logged into a VT and killed the X server.  This is exactly the problem I was trying to avoid. I entered startx but it gave me some BS about an nvidia driver module error.  I rebooted and surprisingly X loaded without any errors.  Alas, I had to open all my programs again.  

What else could I try to restart gnome-shell?

---


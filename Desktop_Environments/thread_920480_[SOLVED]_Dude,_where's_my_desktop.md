---
title: "[SOLVED] Dude, where's my desktop?"
date: 2008-09-15
forum: Desktop Environments
---

### Post by patchin_house on 2008-09-15
O wise ones:

Well, here's a new one for me. This morning, I boot up Xubuntu as usual... and suddenly my desktop isn't there! No icons, no Xubuntu-default wallpaper, just the SCIM sticky and Miro (which is set to auto-start after a successful login).

And I *know*, full well, that I've got stuff on this here hard disk.

Has anyone else had XFCE go bad on them like this? :confused:

And what can I do now to repair the window manager without forfeiting my files and apps?

Anyone?

Philip David
(grateful for having a spare laptop
at a silly time like this)
2008.09.15

---

### Post by mali2297 on 2008-09-15
Press Alt+F2, do you reach a run dialog?

If success, type *xterm* to get a terminal window. Then start the desktop manager with the command 
```
xfdesktop &
```

Have you used Nautilus? In that case, first kill it with
```

pkill nautilus

```

[QUOTE=http://spuriousinterrupt.org/projects/xfce4#faq]Help!  My Xfce desktop disappeared!  It looks like GNOME!  And the desktop menu is gone too!  What do I do?

    * 	You ran nautilus, didn't you?  By default, Nautilus takes over the desktop when it runs.  First you need to kill Nautilus, and then you should run xfdesktop to make sure Xfce's desktop manager is running.  In the future, when you run Nautilus, pass it the --no-desktop option to instruct it to avoid drawing the desktop.  A more permanent solution is to set the gconf key /apps/nautilus/preferences/show_desktop to "false" (the --no-desktop will no longer be required).  This can be done using the graphical gconf-editor, or the command-line gconftool utility.[/QUOTE]

---

### Post by patchin_house on 2008-09-15
Many thanks... in the end I installed two different window managers (BlackBox and WindowMaker), then uninstalled and re-installed XFCE. That restored most but not all of my desktop. The menu bar -- which I suspect is a Gnome component -- is gone now. 

This leads to two questions:

1) Is it advisable to restore or replace it?

and 

2) If replacing it is the right thing to do, then with what?

Philip David
2008.09.15

---

### Post by patchin_house on 2008-09-15
And just like that, it occurred to me: Somehow in the probing to see what else went bad, gnome-panel got uninstalled.

So it's back now. Hopefully for keeps.

And I'll try to pay much better attention to what I add to my recovering penguin. :wink:

*Elkoran dankon* (thank you), mali2297. This is what being a member of the Forums is all about. Support when you need it the most.

Philip David
(no one should do Linux in isolation, much less inertia)
2008.09.15

---


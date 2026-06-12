---
title: "Network Icon bleeds through"
date: 2009-09-04
forum: Desktop Environments
---

### Post by Clive McCarthy on 2009-09-04
The networking icon on the task bar at the top of the screen flashes momentarily (but constantly -- probably every time it's polling the network?) even though I have 'switched off' the task bar with wmctrl. It seems that gnome doesn't fully obey the command I give it via wmctrl? Or maybe it's just the nm-applet networking sub-system?

[COLOR="Red"]system("wmctrl -r\"My Window's Name\" -b add,fullscreen,skip_taskbar");[/COLOR]


I have a full-screen freeglut (v 2.4.0) OpenGL application running in GameMode and I just can't see how to get the network icon to be quiet. I don't want to turn-off networking.

Is there some way of shutting Gnome off entirely from within my program and restoring it when my application exits? I need to keep x-windows running because OpenGL has to run.

I found a solution from another posting:

Re: Remove network icon from panel? 

--------------------------------------------------------------------------------

It's not actually a separate panel applet but is running in the system tray, which is confusing since it's named "network manager applet". I know you can go to 
[COLOR="SeaGreen"]System -> Preferences -> Session and disable the network manager applet there.[/COLOR] 
As long as the regular network manager daemon runs I think your network will still connect fine.

:popcorn:

---


---
title: "Cairo-dock duplicate docks???"
date: 2011-10-23
forum: Desktop Environments
---

### Post by Ghost|BTFH on 2011-10-23
**RESOLUTION:**

Although I am sure there is a more elegant way to do this, I presumed that the issue was in the fact of having originally spawned the cairo-dock, telling it to always launch at startup and then saving the desktop settings on each logout.  My guess is, it kept spawning an additional copy of the cairo-dock.

In order to fix this, I reversed the process by removing ALL cairo-dock spawns, then telling it to save settings.  This gave me a desktop with zero docks.  From there, I went into xfce4-settings-manager (ALT+F2) and then made sure that cairo-dock was added to the auto-start list.  This seems to have stopped all the spawning.
====================================================================================================
Hey all,

Long time since I've asked for help, but switching Distros makes me feel like a noob again. :)

I've stepped away from Ubuntu and switched over to Xubuntu and have been quite pleased with everything - except for one major bug that I cannot seem to find any information about at all on the Internet, nor can I figure out on my own.

What's been done:

Fresh install Xubuntu 11.10
Removal of lower panel and hiding of upper panel.
Installation of Cairo-dock.
Installation of Cairo-dock addons.

What's resulted:

Everything works.
Occasionally opening Firefox and going to a new page will drop me completely out of my x-session and back to login. (I suspect it's drivers and will be verifying that later).  **EDIT:  I have also noticed that performing a *killall cairo-dock && cairo-dock* will also cause the desktop to login screen crash.**
**Cairo-dock spawns 3 copies of itself - one on top of the other.**

It's that last part that bothers me, I'm not really keen on killing 3 spawns of 1 program that I want to keep, every single time I log in.  

Any ideas of what might have caused it, or where to look?  Might there be a configuration file somewhere that just simply has cairo-dock listed 4 times or something?

Any and all help would be, as always, greatly appreciated.

Cheers,
Ghost|BTFH

---

### Post by LewisTM on 2011-10-24
I have experienced that 3 instance problem before.

Solved by removing the autostart entry for Cairo-dock (that's one instance) and disabling saved sessions (that's another). Which leaves one. I don't know where that entry is specified but that's OK.

---

### Post by Frogs Hair on 2011-10-24
I have not used Cairo / GLX   dock for a while , but had similar problem and I solved it by deleting the configuration file and starting over . 

Reinstalling won't work  because  the dock will just use the old configuration until it is removed . As I wrote it has been a while , but I think the folder is in home .hidden folders .

---

### Post by Ghost|BTFH on 2011-10-25
Yeah, I checked out the .hidden folders in ~/home and couldn't find a bloody thing.

So my solution of removing them all, saving and then telling it to start up cairo-dock at start seemed to fix everything and resolved the crashes too...

---


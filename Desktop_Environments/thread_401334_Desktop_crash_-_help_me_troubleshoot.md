---
title: "Desktop crash - help me troubleshoot"
date: 2007-04-04
forum: Desktop Environments
---

### Post by Kisil on 2007-04-04
I'm getting an occasional lockup where my keyboard and mouse stop interacting with the desktop.  Programs continue running, and my cursor moves, but clicking or typing give me no response.  I've tried switching to a different TTY or restarting my window manager, and even those hotkeys do not respond.

What I'm trying to figure out is how to adequately describe this bug, and which program group to report it to.  Does anyone have any insight as to what the problem might be?


I'm running Ubuntu edgy, gnome 2.16.1, and beryl 2.0 with Nvidia drivers 1.0-9746.  I upgraded to edgy and beryl at the same time, so while it wasn't crashing before, I can't isolate a single component.  The problem seems to be more frequent when I'm either switching windows or opening or closing a tab in firefox or gaim.  Total crash frequency is from 1 per 2 weeks to as much as 3 per day.

Also, I have a hunch that instead of having to hard-reboot, I could ssh into my machine and reset gnome from afar.  Anyone know how to set up remote login, or where I'd look to find out how?  Ideally I'd like to open up only a minimal security hole.

---

### Post by Sqwishy on 2007-04-04
If you had a recent xorg update that's probobly the problem, you need to reinstall your drivers, its easiest with envy [[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)] then it should be fine.
this happened to me today and this is what i did.
:D

---

### Post by whitetux on 2007-04-06
I'm experiencing the same thing. Mouse moves, but nothing is responding. It seems it always happens when Firefox is open.

FRUSTRATING. Have to power off to use it again.

---

### Post by Kisil on 2007-04-09
Mine happens most often when firefox is active, but occasionally when I'm using gaim.  I thought it was related to changing tab and window focus, but then it happened this morning when I went to click a link - the address appeared in the firefox status bar (i.e. mouseover event worked correctly), but then my click did not register, and no further events worked.

Can anyone point me towards a good tutorial on setting up SSH access to my machine?

---


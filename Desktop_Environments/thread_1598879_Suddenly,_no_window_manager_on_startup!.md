---
title: "Suddenly, no window manager on startup!"
date: 2010-10-17
forum: Desktop Environments
---

### Post by pmooney78 on 2010-10-17
I restarted my computer this afternoon and noticed that no window manager seemed to be running ... no window borders or close/minimize/maximize buttons, can't click in a window's content area to raise it to the top, etc. Top and bottom panels were largely blank, not operating as expected. Alt+F2 didn't bring up a "Run" box. My normal desktop icons were missing. Restarting multiple times didn't solve the problem.

I ran "gnome-wm &" from a terminal (luckily, I have Tilda auto-startup when I login), and it gives me:

I/O warning : failed to load external entity "/home/patrick/.compiz/session/108cc4b254974f58d3128730370687931300000032870001"

This error message seems to be the same every time I run the command after every reboot. (I'm not absolutely sure, but I think even the long hex string is the same every time.)

Thinking it to be a problem with compiz config files, I opened Synaptic, purged all the installed compiz packages, and then reinstalled them and rebooted. No dice: the same problem is still happening the same way. I've also tried changing the level of desktop effects I'm using, but that doesn't work either.

Any suggestions? I've tried searching the forums for similar problems, but although there are some vaguely similar issues, nothing that resembles this seems to have been satisfactorily solved. It's kind of an annoying problem. No updates have been applied in the last several days, and I haven't installed any new software. I am also not auto-remembering currently running applications on restart.

Currently running Ubuntu 10.04 on an HP Pavilion dv6000 laptop with 2GB of RAM and an Intel Centrino Duo processor, and the NVidia Accelerated Graphics Driver ("version current") is activated in the Hardware Drivers applet.

Any help is much appreciated.

---

### Post by pmooney78 on 2010-10-18
Bump.

---

### Post by 3Miro on 2010-10-18
Go to terminal and temporarily replace compiz with metacity:
```
 metacity --replace 
```
BTW you should be able to do that with Alt+F2 without the need for tilda terminal.

After that, open nautilus, hit Ctr + H to show all the "hidden" files and lookup .compiz. Rename the folder to .compiz_old or _backup or something like that. Then reboot. You will lose all (or most) of your settings for compiz, but it should work again. (synaptic cleans the system files, it doesn't clean config files in your /home/ folder)

---

### Post by pmooney78 on 2010-10-19
Thanks! ... but still no dice. Still having the same error message when using compiz --replace (or, for that matter, metacity --replace) on startup. :(

---

### Post by pmooney78 on 2010-10-21
Never mind ... purging and reinstalling system.

---

### Post by ratxor on 2010-12-08
Hello, I have the same warning in my ~/.xsession-errors file:

I/O warning : failed to load external entity "/home/<...>/.compiz/session/<...>"

I am googling, but not solving yet. Configuration is: Ubuntu 10.10 Netbook Edition, ASUS EePC 900.

---

### Post by pmooney78 on 2011-01-09
No idea. I never managed to figure it out. You're more likely to draw attention if you post a new thread, though.

Good luck!

---

### Post by Krytarik on 2011-01-09
@ratxor: Try to remove/rename both directories, "~/.compiz" and "~/.gconf/apps/compiz". Note that this will definetely unset all your Compiz settings.

---


---
title: "gnome settings daemon error . ubuntu 8.10"
date: 2009-05-11
forum: General Help
---

### Post by alwayshere on 2009-05-11
when i start up i get this error msg

 error starting  gnome settings daemon 
 the settings have been restared too many times 

 gnome will try to restarty settings next time you log in 


any ideas ?

---

### Post by baseface on 2009-05-11
try resetting your system clock.

---

### Post by alwayshere on 2009-05-11
i cant when i put my password in to unlock it i cant adjust anything so there seems to be a problem there somehow have you any ideas

---

### Post by baseface on 2009-05-11
drop to a console and use the "date" command to change your system time.

---

### Post by slash5toaster on 2009-06-01
> **alwayshere said:**
> when i start up i get this error msg

 error starting  gnome settings daemon 
 the settings have been restarted too many times 

 gnome will try to restart settings next time you log in 

any ideas ?

I got a similar error.  According to the man page there are some debug options --debug and -no-daemon
 I tried [INDENT]```
gnome-settings-daemon --debug --no-daemon 
```[/INDENT]from a console
 and I got an error message about segfaults with ffmpeg.
[INDENT] ```
ERROR: Caught a segmentation fault while loading plugin file:
/usr/lib/gstreamer-0.10/libgstffmpeg.so 
 Please either:
- remove it and restart.
- run with --gst-disable-segtrap and debug.
 
```
[/INDENT]I renamed the file to .old and this let the settings daemon start. I have some package dependency errors with ffmpeg and dvdrip, so I will have to resolve those first.
 Try running gnome-settings-daemon from the command line to see where the real problem lies

---


---
title: "Hang on logout/restart/shutdown"
date: 2010-12-25
forum: Desktop Environments
---

### Post by allbread on 2010-12-25
I'm currently running Linux Mint 10 (Ubuntu 10.10) on my Thinkpad W500  and have encountered an annoying issue... essentially I get an  intermittent hang when I attempt to restart or logout. 

This problem has been made more visible as of late possibly due to my  screwing around with the hybrid switcheroo configurations (see: [http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)  if you dare) but I don't know if this is the root cause... at least I  don't recall directly if this problem started only when I made the  changes detailed in the switcheroo procedure. 

What is odd is that when I attempt to reboot via an application (in this  case the UNetBootin utility) everything seems to work fine, however,  attempting to do the same via the main desktop "Menu" usually causes a hang.

Although I've done my best with the details I know the description above  is still vague, however, being relatively new to Linux (at least for  anything beyond a regular user) I'm not sure where to start in terms of  troubleshooting... 

So, in short, where do I start?

---

### Post by WthIteh on 2010-12-25
> **allbread said:**
> So, in short, where do I start?
You could start by checking result of
```
dmesg
```
You may find there error messages about the underlying issue.

---

### Post by allbread on 2010-12-25
Thanks for the suggestion.

I did this and the only error messages I could grep from the file were:

[    2.321362] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[    2.321367] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing F6D8 (len 487, WS 0, PS 4) @ 0xF719
[    3.361344] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[    3.361348] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing F6D8 (len 487, WS 0, PS 4) @ 0xF719

(from the output of dmesg executed after a hard restart)

Any ideas?

There are also a number of log files in /var/log (including a number of older dmesg.* log files)... would any of these be relevant?

In reference to restart/logout/shutdown issues (additionally I cannot "wake" my laptop once it has gone to sleep) what should I be looking for in terms of error messages?

---


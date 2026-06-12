---
title: "Hydrogen Not RESPONDING"
date: 2009-04-06
forum: General Help
---

### Post by WadeH2o on 2009-04-06
Hi everyone I would like some advice and guidance with Hydrogen.  After I launch the program, I can play a beat for about 5 to 8 seconds before it stops playing.  I can move the adjustments and watch the lights turn on or off but no sound. What I then do is close the program then back to the Applications menu to launch it again to only get the same results.  But get this, when I go to shut down my PC the process is interrupted with a small window telling me that Hydrogen is Not Responding, not once but three times! I then force quit so my PC can be shut down. What's going on here?? Can someone please explain.  

Does Ubuntu have a program like Windows Task Manager where I can view which programs are running and their status? 

SPECS:
Ubuntu 8.10
Hydro Version 0.9.3

---

### Post by WadeH2o on 2009-04-07
Am I the only one having this issue?

---

### Post by markbuntu on 2009-04-07
System monitor will do that for you. You can put it in your panel. Right click on the panel and choose add to panel. System monitor can show cpu, network, ram, system load and disk usage in the panel and you can right click on it and open it for a lot more information.

What is happening with hydrogen is that it becomes a zombie and will not respond to commands. You will see it in System Monitor/Processes sleeping. You can kill it by right clicking and choosing kill process.

You should always check system monitor when an application hangs or does not exit properly. You can close the window but that does not necessarily mean the process has exited.

You can also add force quit to your panel to kill misbehaving aplications.

---


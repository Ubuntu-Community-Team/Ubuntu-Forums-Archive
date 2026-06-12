---
title: "Desktop icons and background disappeared"
date: 2014-11-28
forum: Desktop Environments
---

### Post by n0c0d3 on 2014-11-28
Hi,

I accidentally created  lots and lots of files in some folder, which I sent to the trash. Emptying the trash went slow and while doing so the desktop hung, I couldn't click anything. When I finally emptied the trash the desktop remained unresponsive and I rebooted. After reboot I was left with a gray desktop, without background or any icons or files to be seen. All panels (toolbars) which I arranged around the screen are still there and work fine, so is the dektop-folder itself. Several more reboots didn't bring back the desktop, neither does the context-menu work on the desktop. So I'm stuck with this gray desktop. Is there any way to get my normal desktop back again?

Thanks for any  advice,
Bart

---

### Post by ajgreeny on 2014-11-28
It sounds as if **xfdesktop** has stopped running after crashing.

Try looking in settings manager ->Settings and Startup->Session tab, if you can get these to run and you may find xfdesktop is missing from the list of active processes, in which case start it with command **xfdesktop**

Once started it ought to restart immediately if it stops for any reason, but I suspect the crash just baffled your system.  You could just use the command **xfdesktop** and sidestep all the investigatory actions I suggest above; if it works it should be problem over.

---

### Post by n0c0d3 on 2014-11-28
> **ajgreeny said:**
> It sounds as if **xfdesktop** has stopped running after crashing.

Try looking in settings manager ->Settings and Startup->Session tab, if you can get these to run and you may find xfdesktop is missing from the list of active processes, in which case start it with command **xfdesktop**

Once started it ought to restart immediately if it stops for any reason, but I suspect the crash just baffled your system.  You could just use the command **xfdesktop** and sidestep all the investigatory actions I suggest above; if it works it should be problem over.

Yes, this was the case indeed. It was missing from the active processes, and a restart of **xfdesktop** worked out. Did a reboot and it's still okay.

I'm relieved the solution was this simple (I was imagining worst-case scenario's like a reinstall already).

Thank you very much, ajgreeny!

---


---
title: "Gnome Startup Script Problem - No Desktop"
date: 2008-03-30
forum: Desktop Environments
---

### Post by yager01 on 2008-03-30
I have been putting up with this problem for some time now, but I have finally had it as I can not find a solution.

When I upgraded to Ubuntu 7.10 from 7.04, my startup script that I was using to launch XGL was no longer needed.  Unfortunately I did not remove this before completing the upgrade.  When I try to start Gnome in normal mode, the desktop goes to a white screen and there are no menus, icons or anything else visible on the desk.  When I restart Gnome in safe mode, the desktop comes up fine and everything is as I had left it.  When I try to edit the startup scripts, there is nothing to edit in the list.

Is there a useful tool that I can use to edit the startup script from outside of Gnome?  The only tool that I have come across is a command line prompt where you have to know what to change.  Since I don't know the inner workings of the gnome configuration file, I have no idea what command to issue to change the affected key value.

---

### Post by yager01 on 2008-03-31
The issue was resolved.

By reading over several threads, I was able to find the configuration file and despite the description in other threads, it is plainly a text file.  I commented out the offending lines and the problem was solved so that i could then correct the file.

If you run across this and are having the same issue, refer to the following link.

[http://ubuntuforums.org/archive/index.php/t-568995.html](http://ubuntuforums.org/archive/index.php/t-568995.html)

---


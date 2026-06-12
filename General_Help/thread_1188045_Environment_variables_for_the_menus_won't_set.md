---
title: "Environment variables for the menus won't set"
date: 2009-06-15
forum: General Help
---

### Post by Arrowx7 on 2009-06-15
Hello,
I was installing some software on ubuntu 8.10 intrepid, and part of the installation instruction included "source ..." command.  I ran the command "ccp4" and the program opened, so it put the source command in /etc/bash.bashrc, to have it open in every shell.  Next, i put the program into the menu on top, putting command as "ccp4" (program name, and command I used to start it from shell).  When clicking on the menu, it says it cannot find the program.  I tried putting in the full path to the executable, and it failed to execute (nothing happened, no error, nothing).  It's as if the environment variables aren't being set for gnome.  I tried doing this with the shotcut on the desktop (launcher) and same thing.  I installed a different program and got the same scenario.

So it looks like the "source" command in /etc/bash.bashrc is only setting the environment variables in the terminals, but not gnome.  Is there a way to fix this?

Thanks!

---


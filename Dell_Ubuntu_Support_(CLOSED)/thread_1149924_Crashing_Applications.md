---
title: "Crashing Applications"
date: 2009-05-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by skeptics4life on 2009-05-05
I was and still am a PC user.  I know that if an application crashes I can call up the Task Manager with ctrl+alt+del.  I have used the "Force Quit" option before and it has done exactly that, quit an application by force.

My question is regarding full screen applications.  I just downloaded Cube2, a first-person shooter, and when it crashes I have to force my computer to shutdown and reboot.  I have tried alt+F4 and ctrl+alt+del but nothing works. Is there another key stroke or another means of restarting a frozen application without forcing my dell to reboot?

---

### Post by coffeeaddict22 on 2009-05-06
Welcome to Ubuntu!
There's always a way.  You should be able to open a terminal session by entering Ctrl-Alt-F1.
In a terminal, type ```
top
``` that'll show you the busiest processes running on your system.  The leftmost column is usually headed PID; it stands for process ID.  Find the PID of the process you want to finish off.
Hit q to stop top running; then enter ```
kill xxxx
``` where xxxx is the PID you found.  That should make it die.  For more info, in the terminal enter ```
man kill
```

---


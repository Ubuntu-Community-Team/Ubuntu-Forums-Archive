---
title: "[xfce] Launcher strangeness with java programs"
date: 2015-12-04
forum: Desktop Environments
---

### Post by dave-lane on 2015-12-04
Hi all,
I'm having a bit of strangeness with all forms of the launcher (desktop and panel) when it comes to java programs. I add for example IntelliJ Idea from the whisker menu to a panel and it has the following command:
"/home/dave/local/idea-IC-143.381.42/bin/idea.sh" %f

I can take this command and execute it in a terminal and it works fine. But when I press the launcher button a window never shows up. I can see a process that is running that does hog some resources.

I did the same thing with SQLWorkbench (with a manually created) desktop launcher with the following as the command:

/home/dave/local/sqlworkbench/sqlworkbench.sh

In this case when I start it an upstart process starts that hogs around 99% CPU.

All other launchers are working. I'm pretty sure the above were working too but am not 100% sure (as the install is less than a month old).

I'm on 15.10 and installed all updates (including some prompted ones today).

Any one having similar experiences?

Regards,
Dave

---


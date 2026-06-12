---
title: "Locating applications"
date: 2015-11-12
forum: Desktop Environments
---

### Post by chriso0258 on 2015-11-12
Hello,

I'm running Ubuntu Desktop 14.04. In Windows, you can right click on an icon and find the path to the application it calls up. How do I do this in UD? There are a couple of icons ("Startup Applications", and "Ubuntu Software Center") that I want to find the executable. I've tried using which, whereis, and locate but have had no success. What is the best way to accomplish this?

Thanks for your help.
Chris

---

### Post by TheFu on 2015-11-12
The best way is to ask the package manager to list the file locations.
**dpkg-query**

But, I'd start with **which** too. This assumes you've translated the name shown in the GUI to the real program name.   For example, "File Explorer" is really "nautilus."

Next I'd use **find**. Again, this pre-supposes the real program name is known.

The other way is to find the ".desktop" file for the application and look inside.

---

### Post by deadflowr on 2015-11-12
Look in /usr/bin for the executables.

Launchers for applications are in /usr/share/applications
So you can look in there, right click on your application of choice and look at the entry for the command.
The command will be the executable.
Example:
Ubuntu Software Center's command is software-center.
running *whereis software-center *will show as /usr/bin/software-center.

These are where most launchers and executables will be.
But note it does not mean all will be in these places.

---


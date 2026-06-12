---
title: "Upgrade trying to uninstall gnome-shell"
date: 2012-01-18
forum: Desktop Environments
---

### Post by mannyf on 2012-01-18
good day.  Running Ubuntu 11.10 64Bit.  I tried using Unity but found it extremely buggy.  I lost right click, out of control screens etc.  Installed gnome-shell.  VERY HAPPY with it.  However now my machine told me there were upgrades to install and then told me it was going to uninstall gnome-shell.

I do not want to run Unity :-(   How can I tell my machine that I want to use the gnome-shell.  I have attached the screenshot.

Tried google but all I get is how to install gnome-shell and nothing on this.

Any help would be greatly appreciated.  

Manny

---

### Post by jerrrys on 2012-01-20
This is not suppose to happen.  Did you manually remove unity?  Try this.  Open a terminal and enter:

sudo apt-get remove compiz-core

This command will remove unity3d and replace it with unity2d.  And may solve your problem.

---


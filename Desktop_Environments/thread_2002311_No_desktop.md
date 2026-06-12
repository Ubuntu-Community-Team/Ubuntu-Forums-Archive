---
title: "No desktop"
date: 2012-06-12
forum: Desktop Environments
---

### Post by gettinoriginal on 2012-06-12
After trying unity, I decided to go back to gnome.  I logged out, clicked on gnome at the sign in, no desktop, restarted computer with power button, clicked gnome classic, no desktop, same with gnome with no effects.  Now I can't even go back to unity, no desktop!  I am having to type this in windows.  Just for info, I did check synaptics before trying to use gnome and it is installed.  Any advice ??

---

### Post by ajgreeny on 2012-06-12
> **gettinoriginal said:**
> After trying unity, I decided to go back to gnome.  I logged out, clicked on gnome at the sign in, no desktop, restarted computer with power button, clicked gnome classic, no desktop, same with gnome with no effects.  Now I can't even go back to unity, no desktop!  I am having to type this in windows.  Just for info, I did check synaptics before trying to use gnome and it is installed.  Any advice ??
But which parts of gnome were installed?

If you were using unity originally, of course you have gnome; unity is a shell that runs on top of gnome, not in place of gnome.

To run gnome classic desktop you need to make sure you have gnome-panel installed, so boot to the command line, if that's all you get and login with name and password (password will not show on screen as you type) then run command ```
sudo apt-get install gnome-panel
``` There will be several dependencies brought in as well, and then you should be able to boot to classic gnome.

---


---
title: "Lost my disk icons on the desktop"
date: 2011-10-19
forum: Desktop Environments
---

### Post by mpiter on 2011-10-19
After upgrading to Ubuntu 11.10 on a separate test partition but using the same [COLOR="DarkGreen"]/home[/COLOR] partition, I remounted the original 11.04 partition that was not modified during the upgrade test.  I will not upgrade to 11.10. My .gconf directory was messed up in the process.  Using another account than mine, I recovered a [COLOR="DarkGreen"].gconf[/COLOR] and a [COLOR="DarkGreen"].gconfd[/COLOR] directories from a backup made just before the upgrade.  When I logged in again in my account, all external devices such as USB devices were still automounted in /media, but there were no more disk icons on my desktop.  I would like the icons back.

I am using Gnome in classical mode with Compiz in an 11.04 up-to-date environment. [COLOR="DarkGreen"]media_automount[/COLOR] is set to [COLOR="DarkGreen"]true[/COLOR] in [COLOR="DarkGreen"].gconf/apps/nautilus/preferences/%gconf.xml[/COLOR], i.e., in Nautilus.  Where else are the volume icons managed?  Thanks for any piece of information.

---

### Post by meatytaco on 2011-10-19
You should be able to go into your desktop settings and click on the icons you want your desktop to show : Computer, Home, Trash, Network, and Mounted Volumes.

---

### Post by mpiter on 2011-10-19
> **meatytaco said:**
> You should be able to go into your desktop settings and click on the icons you want your desktop to show : Computer, Home, Trash, Network, and Mounted Volumes.

Thanks, that was the parameter [COLOR="Green"]volumes_visible[/COLOR] in [COLOR="green"]gconf-editor[/COLOR].  I do not understand how I could miss it yesternight because I browsed that set of parameters.  I was probably too sleepy.  Thanks a lot.

---


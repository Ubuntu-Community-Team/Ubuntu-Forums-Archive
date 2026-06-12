---
title: "Removing KDE Splash Screen"
date: 2008-05-20
forum: Desktop Environments
---

### Post by Ubuntist on 2008-05-20
A long-time Gnome user, I recently decided to try KDE and installed it with apt-get. After deciding to stick with Gnome for the time being, I tried to remove KDE. I've been mostly successful, but I still get the KDE spash screens when booting up and shutting down, and the Gnome login screen still offers KDE as an option. I've read a number of threads about removing KDE and have used Synaptic to remove all KDE packages that might (as far as I can tell) be relevant, but I'm still getting KDE splash screens.

Could anyone suggest particular packages that I should be sure to remove?  Or any other actions I should take?

---

### Post by dushkal on 2008-05-20
I assume you mean the usplash.

1. You can use update-alternatives to change your splash back to ubuntu-default (can not check that right now as I switched to splashy)
2. Try using Startup Manager to configure USplash.

---


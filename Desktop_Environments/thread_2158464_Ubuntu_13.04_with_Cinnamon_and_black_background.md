---
title: "Ubuntu 13.04 with Cinnamon and black background"
date: 2013-06-29
forum: Desktop Environments
---

### Post by snakeplizzken on 2013-06-29
Hi

Sometimes then I log in the background is totally black (except from the top panel and the Avant Window Navigator dock).
Nothing happens then I right-click the mouse on the desktop.

Opening the filemanager Nemo most of times makes the desktop update correctly - sometimes a restart is necessary.

Can this have something todo with it?
[https://github.com/linuxmint/Cinnamon/issues/696](https://github.com/linuxmint/Cinnamon/issues/696)

It is a great combination otherwise: Ubuntu, Cinnamon and AWN.

If someone has a clue I would be very grateful.

---

### Post by skamlic on 2013-08-09
Did you solve your problem? I have the same issue and have no clue what to do.

Edit: Just found this. Not a solution, but interesting:

After restart, you open File explorer and close it, repeat one more time. Background will show again.

---

### Post by crazymonkey05 on 2013-08-09
i had a similar problem i discovered that my ubuntu-cinnamon install was in fail safe mode and loaded a minimal GUI but a re install fixed it for me...

---

### Post by snakeplizzken on 2013-08-09
No. Haven't found a solution to this problem yet.
I have found solutions to a number of other issues though:

1. The SSD is too fast for lightdm
Most of the time the login screen will not show up on startup.
Only a black screen and a black cursor is displayed.
Adding a "sleep 2" to /etc/init/lightdm.conf solved that problem.

2. The screen dims after a while totally disregarding the settings in Screensaver & Lock Settings.
Running:
> gsettings set org.gnome.desktop.screensaver idle-activation-enabled false
solved that problem.

But I think there could a problem with having both Nemo and Nautilus handling the desktop.
Because
> gsettings get org.gnome.desktop.background show-desktop-icons
true

> gsettings get org.nemo.desktop show-desktop-icons
true

I don't think both keys should be true.
Like it says here:
[http://www.fandigital.com/2013/01/set-nemo-default-file-manager-ubuntu.html](http://www.fandigital.com/2013/01/set-nemo-default-file-manager-ubuntu.html)

Maybe one of them should be disabled via set.

---

### Post by snakeplizzken on 2013-08-09
> gsettings set org.nemo.desktop show-desktop-icons false
Might do the trick.

Further testing has made med confident that this solves the problem.
Enabling nemo desktop handling (together with Nautilus):
> gsettings set org.nemo.desktop show-desktop-icons true
after that log out and login again and the desktop is black until Nemo is started manually.

---


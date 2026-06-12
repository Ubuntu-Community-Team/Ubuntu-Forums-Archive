---
title: "display/cairo"
date: 2009-06-17
forum: General Help
---

### Post by Feelin_froggy8877 on 2009-06-17
Since I done a fresh install cario-dock has been acting funny. I have it set to autostart. But when I change my screen res (since I can't save nvidia setting to xorg with out a bunch of problems). When I try to set the dock to the bottom of the screen it jumps back to the middle. I have to restart it to get it to set at the bottom of my screen. 

As for the nvidia settings, I have posts here about that too. Still no resolve.

---

### Post by Feelin_froggy8877 on 2009-06-18
(bump) No 1 else having, or had this problem?

---

### Post by derklempner on 2009-06-18
I had more than my fair share of Cairo problems after a recent upgrade of the software.  Using my secondary "media" PC as a testbed, I found the proper way to be able to configure it to my liking once more.

First, completely remove the old install of Cairo.  From the command line:

```
sudo apt-get remove --purge cairo-dock
```

Now reboot your system.

After reboot, install the necessary repository for the current Cairo release.  Add the following line to your sources.  First, open the sources.list file:

```
gksudo gedit /etc/apt/sources.list
```

At the end of the file, choose the proper respository to add, based on the Ubuntu release you're running:

```
deb http://repository.cairo-dock.org/ubuntu jaunty cairo-dock  # For Ubuntu 9.04

deb http://repository.cairo-dock.org/ubuntu intrepid cairo-dock  # For Ubuntu 8.10

deb http://repository.cairo-dock.org/ubuntu hardy cairo-dock  # For ubuntu 8.04
```

Finally, update your sources and install the newest version of Cairo:

```
sudo apt-get update
sudo apt-get install cairo-dock cairo-dock-plug-ins
```

That should do it for you.  Please note that all these steps are covered in the Ubuntu community documentation at the link located [[COLOR="Red"]_here_[/COLOR]]("https://help.ubuntu.com/community/CairoDock").

---


---
title: "Booting without X"
date: 2008-12-14
forum: General Help
---

### Post by Maverick1712 on 2008-12-14
Hi all

I am starting to use my desktop as more of a server than a desktop computer, and was wondering how I would go about making it go into a non-graphical instance when booted, aka not starting x by default, but I can start x when I see fit. Please don't suggest just installing ubuntu-server, as I couldn't get my wireless USB working properly with it.

Cheers,
Adam

---

### Post by albinootje on 2008-12-14
You can install rcconf and/or sysvconfig and remove gdm from the list.

---

### Post by Maverick1712 on 2008-12-14
What list are you referring to that I should remove GDM from?

---

### Post by Bucky Ball on 2008-12-14
The simple answer is to install the server edition which has no desktop! You can add the packages from there (including a basic environment like OpenBox or Xfce). You could backup what you need to keep, install server edition and away you go.

---

### Post by Maverick1712 on 2008-12-14
The problem with installing server is my usb wireless card doesn't work right away with server, whereas it does with desktop, so I was hoping to try and fool the box into thinking it was a server. Any idea why my wireless card would work with desktop but not server?

Cheers,
Adam

---

### Post by Bucky Ball on 2008-12-14
> **Maverick1712 said:**
> Any idea why my wireless card would work with desktop but not server?

Cheers,
Adam

Not sure, but if you could figure that out you're halfway there. You could identify what packages you are using to get your USB wireless up in desktop, save them in your backup and then put them back in place or download them in the fresh server install.

As I say, you need to backup the packages you are currently using and want to keep then put them back. You may want to do a search for 'AptOnCD' which will allow you to do this.

---

### Post by gsmbk on 2008-12-14
I guess moving to the Server edition is a good choice if you're going to use the machine as a server.

To solve you USB wireless card problem, try to see what is the driver that is supporting it on your desktop edition. See what is the package that support it, and simply install it on the server edition, from the Desktop repository, and it will just work fine with you as the desktop edition, making sure that you install all the needed dependencies.

---

### Post by albinootje on 2008-12-14
> **Maverick1712 said:**
> What list are you referring to that I should remove GDM from?

The list in rcconf or sysvconfig.

I think rcconf is the faster option compared to sysvconfig.
After removing gdm from the "boot start-up" programs list, you can choose to do : sudo /etc/init.d/gdm restart or just for your user : startx

You can also refrain from installing rcconf and/or sysvconfig, and read :
man update-rc.d

---

### Post by The Cog on 2008-12-14
To stop GDM from starting at startup, you can remove the symbolic link /etc/rc2.d/S30gdm, or perhaps rename it to XS30gdm (so you can find it and rename it back again). Unless it starts with 'S' it won't be started at boot.

I think you will find that the network-manager applet only works when a user is logged in, so if you want the wireless to work without having to start a GUI, you should perhaps replace it with wicd [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) which does work and connect to the wireless network without a GUI running or anybody even logging in. Although I don't know how to actually configure it without the GUI.

---

### Post by kevdog on 2008-12-14
If you are going to go with an x terminal -- something similar to booting into recovery mode, you should probably get used to making a manual network connection.  Its possible wicd will work this way, but I've never tried it (theoretically it should be possible).  Its also just possible to put your manual wireless configuration commands in a script file and call the script file from rc.local as well.

---

### Post by The Cog on 2008-12-14
Wicd does work that way, (it runs as a daemon/service) and correctly connects to the strongest access-point after boot. I tested it by disabling GDM as described above. I do like your link to manual confgiuration though - I've never seen instructions on how to do that before.

---


---
title: "Debian"
date: 2005-12-11
forum: Desktop Environments
---

### Post by CharlieC on 2005-12-11
I tried to install Sarge Debian. Much to my surprise I did not get a GUI when it was done. I have read all the Debian documentation I could find I am still a bit confused. I think I can get a GUI by loading the desktop packages during the installation process, or do I have to downolad Xwindow (sorry I'm new) or something like that.
     Anyone who has installed this please let me know if I am on the right track.

THanks
Charlie

---

### Post by Zelut on 2005-12-11
Uhm, well first I'm wondering why you're asking Debian Sarge support questions in the Ubuntu Forum... but we'll see what we can do.

I'm assuming after you boot you end with a login prompt at the terminal?  Have you tried running 'startx'?  I would assume (although I've never installed Sarge) that X is installed by default, its just a matter of running it.  It may not be listed to run automagically.  

Give that a try & get back to us..

---

### Post by kairu0 on 2005-12-11
Unlike Ubuntu, Debian does not automatically include a complete, working desktop by default. If you need a GUI, then you should specify to install its components (Gnome, KDE, WindowMaker, whatever) during the install. After the install, you can still install these packages, though.

---

### Post by kairu0 on 2005-12-11
[QUOTE=kuyaedz]Uhm, well first I'm wondering why you're asking Debian Sarge support questions in the Ubuntu Forum... but we'll see what we can do.[/QUOTE]

That was my first thought, too.

---

### Post by CharlieC on 2005-12-12
Hi;

    Thanks, I did not know there was a Sarge support. I will look for that. I asked here because Ubuntu is based on Debian.

Charlie

---

### Post by RAOF on 2005-12-12
Ubuntu is indeed based upon Debian.  It's debian, but with current software, and a set-up-by-default GUI.  Oh, and a whole host of cool, user-friendly stuff.  Maybe you should try installing Ubuntu instead ;)

---

### Post by aysiu on 2005-12-12
From [the Debian installation manual](http://www.debian.org/releases/stable/i386/ch07s02.html.en#install-packages): > So, you have the ability to choose tasks first, and then add on more individual packages later. These tasks loosely represent a number of different jobs or things you want to do with your computer, such as **&#8220;desktop environment&#8221;,** &#8220;web server&#8221;, or &#8220;print server&#8221;[7]. Section C.3, &#8220;Disk Space Needed for Tasks&#8221; lists the space requirements for the available tasks.

Once you've selected your tasks, select Ok. At this point, aptitude will install the packages you've selected. You want **desktop environment**.

P.S. Ubuntu *is* Debian-based, but it's also a different distro. One of the main differences between distros is how their installer works and what default packages are in that installation.

---

### Post by migueljacq on 2005-12-12
My Debian Sarge dvds installed both Gnome and KDE. \o/

---

### Post by az on 2005-12-12
su
apt-get install gnome x-window-system-core gdm

If that fails, 

w3m debianhelp.org
:)  (They rock!)

---

### Post by tuxy on 2005-12-12
Or you can try typing "tasksel" at command console. You get the options to choose the different applications, even the X windows.

---

### Post by unisol on 2005-12-12
debian only installs the base system by default log in as root type root password at command line type base-config you will then be able to install xserver then your window manager

---


---
title: "Removing Window Managers"
date: 2006-01-14
forum: Desktop Environments
---

### Post by blaise69 on 2006-01-14
Hi there chaps,

I installed Ubuntu a while ago on my old Dell Latitude laptop, I then became curious about using the KDE and XFCE desktops, I read in the forums how I could install these Window Managers without having to install Kubuntu or Xubuntu by using apt-get or the Synaptic Package Manager, which is what I did, it installed many new applications as well as the window managers.

I've come to a point now where I've decided that I don't want to use Gnome anymore and would rather stick with KDE, is there a way I can remove the XFCE and Gnome desktops and the applications they installed (especially in the case of XFCE) without ruining my current install?  I'd rather not have to download Kubuntu and start from scratch again, and at the moment I've got loads of applications some of which do the same thing.

TIA

Blaise.

---

### Post by curuxz on 2006-01-14
In prinicipal yes, but thats asuming you only want the KDE alternatives and not a mix match of the pest package. Go into synaptic and search for gnome, somewhere there you will find something saying the gnome desktop enviroment meta package, remove that and they all go. Xfce is a bit more manual since you will have to deselect the packages one by one, tho if you find the base package (i think just called Xfce) then they all should automaticly go since they depend on it. 

WARNING!!! This process may break your install and take away packages you need. My advice is leave them in.

---

### Post by GTvulse on 2006-01-14
The safest way to do such radical transition is to purge a base library that all other related packages would depend on, in the case of removing gnome and xfce you want to eliminate gtk+. As well, you want to install the kubuntu-desktop metapackage. To prevent breakage I strongly recomend you do this **without** a graphical interface. 
[list]
[*]Hit ctrl-alt-f[1-6] your choice of function key.
[*]At the console become root (with "[font=monospace]sudo su -[/font], for example. There are several methods, this one gives you a clean operating environment).
[*]Kill the graphical desktop with [font=monospace]/etc/init.d/gdm stop[/font]
[*]Remove gtk: [font=monospace]dpkg -r libgtk2.0-0[/font]
[*]Remove glib: [font=monospace]dpkg -r libglib2.0-0[/font]
[*]Reinstall kubuntu-desktop: [font=monospace]apt-get --reinstall install kubuntu-desktop[/font] Don't be surprised if some gtk and gnome packages are installed again.
[*]Reboot.
[/list]

---


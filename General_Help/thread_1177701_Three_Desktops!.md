---
title: "Three Desktops!"
date: 2009-06-03
forum: General Help
---

### Post by Shibblet on 2009-06-03
I currently have Ubuntu 9.04 installed on my desktop computer.  I want to add the Kubuntu-desktop and the Xubuntu-desktop variants.

The idea is to choose which one I want at the login screen.

The problem that I am having is that the KDE apps load into the Gnome menu, and XFCE, etc.  

What's the best way to keep the apps from loading into one user interface or the other?

And Secondly, are there any variations in the actual OS (or Kernel)?  Are the only differences between Ubuntu, Kubuntu, and Xubuntu the desktop environment?

---

### Post by Greenwidth on 2009-06-03
I don't think there is a way to separate the apps like that, Gnome apps will be available in KDE and vice versa. 
You could just uninstall the ones you don't want, or have a partition for each.

---

### Post by pawnrocket on 2009-06-03
I don't know why you wouldn't want them but the best I can do is tell you how to get rid of them in gnome. 

Right Click on you Menu
Click Edit menu
and remove the checks on everything you don't want to show up.

---

### Post by Shibblet on 2009-06-03
I just want to keep the KDE specific stuff in KDE, likewise with Gnome and XFCE.

I know the programs will normally run in any environment, but I just want to keep the menus like they were default.

---

### Post by CatKiller on 2009-06-03
> **Greenwidth said:**
> I don't think there is a way to separate the apps like that, Gnome apps will be available in KDE and vice versa.

There is, but it means editing the files by hand. Launchers are defined by [.desktop files]("http://standards.freedesktop.org/desktop-entry-spec/latest/"). Menus are defined by [.menu files]("http://standards.freedesktop.org/menu-spec/latest/").

Most of the automatically-created launchers are in /usr/share/applications. User-specific changes to the menu entries are in ~/.local/share/applications.

You can control which entries are displayed in which Desktop Environment with the OnlyShowIn or NotShowIn list attributes. A number of applications will already have these attributes set.

---

### Post by Greenwidth on 2009-06-04
I stand corrected :)

---

### Post by ad_267 on 2009-06-04
Yeah the KDE menu editor has an option for "Only show in KDE" for each item.

---

### Post by Shibblet on 2009-06-06
Hey, that worked out great!  I did however notice a performance decrease with KDE.  Do I need to re-load the Nvidia drivers, or is KDE just slower than Gnome?

---


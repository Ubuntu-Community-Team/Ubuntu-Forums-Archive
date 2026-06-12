---
title: "Quick Question"
date: 2008-01-23
forum: Desktop Effects &amp; Customization
---

### Post by Fraser from Scotland on 2008-01-23
Can someone tell me the what these do and if they can be used on Ubuntu?

1)xfce
2)Fluxbox
3)E17

Thanks, Fraser.

---

### Post by Fraser from Scotland on 2008-01-23
Bumpity bump bump

---

### Post by wookietim on 2008-01-23
I think xfce is a desktop environment... don't quote me on that (This also serves to bump the thread up, since I'd like to know the answers too).

---

### Post by Achtung on 2008-01-24
Xfce is a desktop environment, like Gnome and KDE, and like others, it offers a window manager, a file manager, a set of themes and everything needed to manage the desktop. 

Enlightenment and fluxbox are window managers, which control the way you open windows and the placement and appearence of opened windows. 

All 3 can be used with ubuntu. Check out the Xubuntu, OpenGEU and Fluxbuntu projects.

---

### Post by RedSquirrel on 2008-01-24
You can use all three on Ubuntu.

For Xfce, the xfce4 metapackage will install the core of Xfce.

```
sudo apt-get install xfce4
```

For Fluxbox:

```
sudo apt-get install fluxbox && sudo update-menus
```

I'm not sure of the package name for Enlightenment, but you can look it up. I know there's one for E16, but I'm not sure if E17 is in the Ubuntu repositories.

In all three cases, you can run them by choosing the one you want from the Sessions menu at the login screen.

---

### Post by theRightNee on 2008-01-24
just curious, what window manager does ubuntu use by default? metacity? gtk? all a bit confusing, thanks!

---

### Post by smartboyathome on 2008-01-24
> **Achtung said:**
> Xfce is a desktop environment, like Gnome and KDE, and like others, it offers a window manager, a file manager, a set of themes and everything needed to manage the desktop. 

Enlightenment and fluxbox are window managers, which control the way you open windows and the placement and appearence of opened windows. 

All 3 can be used with ubuntu. Check out the Xubuntu, OpenGEU and Fluxbuntu projects.

Actually, E17 is a desktop environment, not a window manager. And Ubuntu uses Metacity by default, and when compiz is enabled, GTK-Window-Decorator. You can install it by using [these instructions]("http://linuxmint.com/wiki/index.php/Install_Enlightenment_E17_desktop_on_Mint"), which work for ubuntu, but are more dated and aren't the latest code (but are more stable).

---

### Post by Achtung on 2008-01-25
> **smartboyathome said:**
> Actually, E17 is a desktop environment, not a window manager. I stand corrected. From the E17 website: [QUOTE=http://www.enlightenment.org/p.php?p=about&l=en]While we are best known for the Enlightenment Window Manager itself there is a long history of providing advanced libraries and tools to support the window manager and other applications, such as Imlib, Imlib2, and FNLib which extend far beyond the window manager itself in scope.[/QUOTE]
Good catch!

---

### Post by RedSquirrel on 2008-01-25
[http://www.enlightenment.org/p.php?p=about&l=en](http://www.enlightenment.org/p.php?p=about&l=en)

> DR17 of the Enlightenment window manager represents an evolution into the next generation of desktop environments: the desktop **shell**.


:)


Just to add to what I mentioned above about Xfce: After installing the xfce4 metapackage, it is worthwhile to search the repositories for other xfce-related packages to see if there's anything else you might want. xfce4-terminal is quite nice, for example.

---


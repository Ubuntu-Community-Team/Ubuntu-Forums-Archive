---
title: "How to install another desktop without extra packages?"
date: 2011-03-03
forum: Desktop Environments
---

### Post by Shiryu on 2011-03-03
Hello
I want to know how to install KDE on Ubuntu and Gnome on Kubuntu.
The commands
apt-get install ubuntu-desktop
apt-get install kubuntu-desktop
are not the solution, because they install all distro packages, and I want only the base of desktops KDE and Gnome.

I can install LXDE with
apt-get install lxde
instead of
apt-get install lubuntu-desktop

I can install Xfce with
apt-get install xfce4
instead of
apt-get install xubuntu-desktop

However, I could not do the same with KDE and Gnome.

Thanks

---

### Post by deconstrained on 2011-03-04
Correct, because kubuntu-desktop and lubuntu-desktop (etc) are (if I'm not mistaken) metapackages that select all the amenities of their respective distros.

Take a look at the dependencies of that package using 'apt-cache show kubuntu-desktop' and cherry-pick. I think that kde-window-manager and kdelibs would be a good place to start, and 'kdm' if you want your login screens to be KDE-managed.

---

### Post by spook1980 on 2011-03-04
gnome:
sudo apt-get install gnome-core

kde:
sudo apt-get install kde-plasma-desktop

---


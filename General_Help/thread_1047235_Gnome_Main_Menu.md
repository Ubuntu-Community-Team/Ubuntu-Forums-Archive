---
title: "Gnome Main Menu"
date: 2009-01-22
forum: General Help
---

### Post by krnekhelesh on 2009-01-22
Hi,

I wanted to make ubuntu's default menu look like SUSE gnome menu. I googled around and found it in this site link below
[http://ubuntu-tutorials.com/2007/01/31/consolidate-your-gnome-menus-with-gnome-main-menu-ubuntu-610/](http://ubuntu-tutorials.com/2007/01/31/consolidate-your-gnome-menus-with-gnome-main-menu-ubuntu-610/)

However when I run the command 
```
sudo aptitude install gnome-main-menu
```

I get the following message
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  gnome-main-menu libslab0{a} 
The following packages will be REMOVED:
  libamrnb3{u} libamrwb3{u} libartsc0{u} libggi-target-x{u} libggi2{u} 
  libgii1{u} libgii1-target-x{u} libglide2{u} liblzo2-2{u} libsvga1{u} 
  libxvmc1{u} mplayer-skins{u} 
0 packages upgraded, 2 newly installed, 12 to remove and 0 not upgraded.
Need to get 290kB of archives. After unpacking 3682kB will be freed.
Do you want to continue? [Y/n/?] 
```
[B][U]
Are the packages above which will be removed important??? Can I proceed with the installation?[/U][/B]

---

### Post by xentro on 2009-01-22
Aptitude detects that those libraries are no longer needed, so he tries to remove them.

No problem with that

---

### Post by krnekhelesh on 2009-01-22
I asked because, before when I tried installing some audio software, it removed my ubuntu-desktop package, and everything screwed up after that.

Since then, I'm always carefull at what library packages it removes.

---

### Post by malfist on 2009-01-22
The ubuntu-desktop package is a meta package and doesn't actually do anything. Basically what it does is it tells apt that it depends on these packages, however uninstalling ubuntu-desktop won't actually do anything to your system, as long as the libraries it installes remain (with a few exceptions)

---

### Post by Tomatz on 2009-01-22
Just use **apt-get** instead of **aptitude** if you are worried ;)

---


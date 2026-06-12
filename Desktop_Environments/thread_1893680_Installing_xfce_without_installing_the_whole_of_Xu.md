---
title: "Installing xfce without installing the whole of Xubuntu, is it possible?"
date: 2011-12-10
forum: Desktop Environments
---

### Post by Dingbats on 2011-12-10
I've been trying to get used to the whole Gnome 3 thing with Unity and all, but no, I just can't.  Xfce looks nice, but if I install xubuntu-desktop on top of Ubuntu, I'll install lots of unnecessary programs like Abiword and whatnot, that I neither need nor want.  I just want the window manager, so everything looks nice again.

Is there any way to install just pure xfce in Ubuntu 11.10 without clogging up the application menu with stuff I don't need?

FYI: Yes, I've tried fallback mode.  Does not do what I want.

---

### Post by nothingspecial on 2011-12-10
```
sudo apt-get install xfce4
```

---

### Post by matt3839 on 2011-12-10
> **nothingspecial said:**
> ```
sudo apt-get install xfce4
```
Also, install xfce4-goodies if you want extra software like the task manager, terminal emulator, etc. and gvfs if you want trash functionality to work.

---

### Post by Bucky Ball on 2011-12-10
You can go all the way and do a Ubuntu minimal install. You install only the packages you want and in your case you would add xfce4 to the list of packages to install (not Gnome or Unity). That way you will get no packages from Xubuntu, except the ones you have selected.

The minimal install installs only enough to get you up and online (unless you tell it otherwise) and once online you can install stuff from Synaptics as per normal and as required. 

I generally just install Thunderbird, Firefox, Xfce4 and a couple of other things, enough to get me started, and work from there. ;)

---

### Post by Dingbats on 2011-12-11
> **matt3839 said:**
> Also, install xfce4-goodies if you want extra software like the task manager, terminal emulator, etc. and gvfs if you want trash functionality to work.
Thanks, both of you!  Will this be easy to uninstall in case it screws things up or I change my mind or whatever?  No biggie if it isn't, but it would be comforting.

> **Bucky Ball said:**
> You can go all the way and do a Ubuntu minimal install. You install only the packages you want and in your case you would add xfce4 to the list of packages to install (not Gnome or Unity). That way you will get no packages from Xubuntu, except the ones you have selected.
Oh, had I known!  I'm a bit reluctant to reinstall a new Ubuntu for the fourth time in two days, but if the xfce install doesn't work out properly, that's the way I'll go.

Also, if I just apt-get xfce4 (and the goodies), will xfce appear as a choice in the dropdown menu at the login prompt?

---

### Post by nonamedotc on 2011-12-11
The only thing you *might* dislike in doing
```
 sudo apt-get install xfce4 
``` on a full ubuntu install is that you might have a few things twice over. I personally did not like that at all.

You might be better off doing minimal install and then getting *only* xubuntu packages ... Of course, you could also uninstall other unwanted items after xfce install.

---

### Post by Dingbats on 2011-12-11
> **nonamedotc said:**
> The only thing you *might* dislike in doing
```
 sudo apt-get install xfce4 
``` on a full ubuntu install is that you might have a few things twice over. I personally did not like that at all.

You might be better off doing minimal install and then getting *only* xubuntu packages ... Of course, you could also uninstall other unwanted items after xfce install.
I just did sudo apt-get install xfce4, and ran into nothing too inconvenient.  I'll just have to avoid Nautilus, since it changes my desktop background, but Thunar will be fine.

---


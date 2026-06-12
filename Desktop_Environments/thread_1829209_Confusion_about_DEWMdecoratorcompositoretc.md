---
title: "Confusion about DE/WM/decorator/compositor/etc"
date: 2011-08-20
forum: Desktop Environments
---

### Post by kristianz on 2011-08-20
Hi!

I know there are several components that make up whatever it is that appears on my GUI. How can I tell exactly what's currently running on my desktop right now? I know I'm running XFCE (Xubuntu) and Compiz. But what about window manager and window decorator (is that the same thing)?

Compiz can be a "compositor" but also function as window manager and window decorator (?). Also, gtk can be window decorator (but not manager?). Then there's XFWM and Metacity (I have Gnome installed as well, but running an XFCE session), which are window managers (and also decorators?).

So I have all these software components available (Compiz, gtk, XFWM, Metacity), all of which can fill one or more roles (window manager, decorator, compositor). How can I tell which is filling which role at this moment?

---

### Post by 3Miro on 2011-08-20
Wow, lots of confusion. 

Window Manager is the program that sits on top of everything else on your Desktop Environment. The most common Windows Managers are: Compiz (default for Ubuntu), Metacity (default for Gnome 2), Gnome-shell (default for Gnome 3), xfwm4 (default for XFCE), Kwin (default for KDE) and OpenBox (default for LXDE).

Most WM have their own decorators, however, Compiz is the exception. Compiz can use one of two decorators: gtk-windows-decorator which mimics Metacity and is used by many people combining Gnome 2 and Compiz, or Emerald which is more shiny but also more resource hungry. Development on Emerald has pretty much stopped and sometimes finding themes is hard, also using Emerald can be buggy.

Composition is a function of the WM that allows for transparency and other effects. Most WM can turn composition on/off, except for Compiz, which is only for composition on. Xfwm4 and Metacity support simple transparency effects. Compiz and Kwin support many shiny effects. Gnome-shell supports only a few extra effects compared to Metacity, but Gnome-shell is still new and more effects will be added in the future. OpenBox does not support composition, although there is a way to hack that at the level of Xorg (don't do it unless you know what you are doing).

GTK is a toolkit, basically a collection of libraries that let you easily make applications with consistent look. The two most used toolkits are QT for KDE and GTK for Gnome, XFCE and LXDE (Gnome 3 uses GTK3 and all the others use GTK2).

Unity 3D is just modified Compiz. Unity 2D is a separate WM with simple composition. Unity 2D is designed to give the same interface as Unity 3D, however, with only minimal composition so that it can be used on systems without good graphics.

If you want to see which applications are currently running, you can use gnome-system-monitor. If you have Gnome, it should be installed by default.

---

### Post by kristianz on 2011-08-21
Thank you! That was well explained and cleared the confusion.

---

### Post by 3Miro on 2011-08-21
> **kristianz said:**
> Thank you! That was well explained and cleared the confusion.

Glad to help. If you have no more questions, you can mark the thread as "Solved".

---


---
title: "Gnome-App-Install Error."
date: 2005-12-02
forum: Desktop Environments
---

### Post by Strag0 on 2005-12-02
My App-Install has stopped working! I ran the executable in terminal and got an error. I'm new to Linux and really haven't a clue how to fix this.

> Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 41, in ?
    from AppInstall import AppInstall
  File "/usr/lib/gnome-app-install/AppInstall.py", line 30, in ?
    import gtkmozembed
ImportError: libgtkembedmoz.so: cannot open shared object file: No such file or directory


Any ideas?

Thank you!

---

### Post by aysiu on 2005-12-02
Can you use apt-get or Synaptic Package Manager?

---

### Post by Strag0 on 2005-12-03
[QUOTE=aysiu]Can you use apt-get or Synaptic Package Manager?[/QUOTE]

At the time, yes I could. However, I tried to reinstall Ubuntu since I wanted to repartition the hard drive once more. That caused a whole slew of problems. One that I solved dealing with the MBR, but now I'm having User creation issues with the installer. So I guess it's out of the frying pan and into the fire!

Thank you thought!

---

### Post by Twillis on 2006-02-18
I'm having a similar problem. When I try to launch Add Applications from both, Applications and System, it does not launch. I then tired to launch it from a terminal and I recieved this error.

root@ubuntu:~ # gnome-app-install
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 22, in ?
    import gtk, gtk.glade
  File "/usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 37, in ?    from _gtk import *
RuntimeError: could not open display

When I try to run apt-get it says that my gnome-app-install is up to date.
      root@ubuntu:~ # apt-get install gnome-app-install
      Reading package lists... Done
      Building dependency tree... Done
      gnome-app-install is already the newest version.
      0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I also tired to uninstall it but I can not because of the Ubuntu-desktop depencies.

I also tired reinstalling it through Synaptic, but with no luck.

---


---
title: "install minimal"
date: 2006-04-19
forum: Desktop Environments
---

### Post by bbarrons on 2006-04-19
I am trying to install edubuntu and am having a hard time getting it finished. How do I do an install that would install the minimal base system to get the desktop up? I can then finish the install after boot. Is this possible?
thanks
Bill

---

### Post by sYs^ on 2006-04-19
> To install a base system, once you have booted from the install cd, type: server

Install a Lightweight System

A good way to install a lightweight (graphical) system is to do a server install (see the above section) and then install some minimal lightweight components.

Some examples are:

sudo apt-get install gdm x-window-system-core xterm icewm menu mozilla-firefox abiword synaptic

This installs a lightweight graphical system using the IceWM window manager. From the command line, simply type

startx

and icewm will start up in tty7.

sudo apt-get install wdm x-window-system-core xfce4 mozilla-firefox synaptic

This installs a system running XFCE. If you consider this, bear in mind that the Xubuntu project might also be a viable option for you.

or even

sudo apt-get install fluxbox x-window-system-core xdm dillo synaptic

This is the lightest installation possible, which uses Fluxbox as its window manager.

[https://wiki.ubuntu.com/Installation/LowMemorySystems](https://wiki.ubuntu.com/Installation/LowMemorySystems)

I hope it helped.

---

### Post by bbarrons on 2006-04-19
Thanks for the help. I had to break up the apt-get install because none of the windows managers would install. still downloading what I could get. I will have it up and running soon just needed a bump in the right direction.
thanks
Bill

---


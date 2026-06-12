---
title: "After installing kde-plasma-desktop from ubuntu, endless Kubuntu-logo screen-no login"
date: 2011-11-16
forum: Desktop Environments
---

### Post by Khufucius on 2011-11-16
Hi guys,

Problem: I installed the kubuntu-plasma-desktop/netbook package from the GUI software tool in Ubuntu 11.10 (using process described here: [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)), and after rebooting, I can't get to the login splash screen.  I just see the "kubuntu" logo, with a progress bar of sorts, filling up over and over again.  No login screen.

The OS loads properly, though -- If I log into a non-gui TTY, I can move through the filesystem and run commands normally.

I'm not sure if the X server is starting up right -- even though it looks like I have the beginnings of a GUI (kubuntu logo) on TTY7, if I switch to TTY6 and log in and run "startx", it doesn't throw any errors.

Running startx on another TTY just pops me into a Gnome desktop session.  I thought this was weird, because whenever I've had a malfunctioning GUI session in the past, trying to launch X server in another TTY always returns an error about some Xorg.config thing being locked by another process (I assume the malfunctioning GUI in TTY7).  But not in this case -- I can launch X from other TTYs without a problem.

Unfortunately, X/Gnome seem to drop me into a limited gnome session -- it only has a top menu bar which doesn't list all the apps, so I'm limited to working with what I see on my desktop.  Still, I can successfully launch GUI programs (e.g. gedit) from here, so it might just be that running "startx" only starts the most basic gnome stuff, and not the side-menu or other startup items.

When I run "top," I see something called kplasmoid running (taking up a few % of CPU).  When I try to kill this process, the system tends to hang completely and I have to do a hard reset.

Any ideas on how I can get KDE working?  Or at least remove it completely and go back to my Gnome splash screen?  I've tried doing a sudo apt-get remove kubuntu-desktop/kde-plasma-desktop, but those seem to be pointer packages that don't actually uninstall anything else.

Right now I can't really use my machine, and I've invested a ton of time in getting the dev environment set up just the way I like it.

Can anyone help?

Thanks in advance!

-K

---

### Post by Khufucius on 2011-11-17
Non?
Thinking it might be some kind of hardware conflict with a kde library (hey, ya never know...), I installed Kubuntu on another partition.  Works fine.  Guess that rules out the hardware.

Any ideas?

-K

---


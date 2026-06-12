---
title: "Custom Gnome Install"
date: 2008-04-15
forum: Desktop Environments
---

### Post by jej2003 on 2008-04-15
So I have seen  several posts asking for a gnome-light installation but have yet to see anything in this regard.  I know I can go through the process to install just the pieces I ma interested in, but was wondering if there was a list of what is currently in the ubuntu-desktop meta package so I could build my own gnome installation with just what I want?  

Also is there a reason why a gnome-light package does not exist?  It would seem this would be a trivial task for the maintainers to put together.  If there is no good reason why this does not exist are there any documents on how to go about building a meta package?

---

### Post by kerry_s on 2008-04-15
how about you just install the base, then just enough to get you to the gui, from there you just look in synaptic at what ubuntu-desktop wants to install, you click on it mark it for install look what it wants to grab, then cancel.

base install
sudo apt-get install xorg gdm synaptic gnome-core
reboot(ctrl+alt+delete)

i'm sure you can figure it out from there.

---


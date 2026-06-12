---
title: "title bars disappear and reappear and missing icons on desktop title bar"
date: 2008-10-14
forum: Desktop Environments
---

### Post by robert.corkum on 2008-10-14
okay I've worked on a few os's I run my servers on another flavour but got a new laptop and thought i'd give ubuntu a spin as I love playing I love the os. it has a few nuiances I am getting used to after working with other flavours (having to keep logging into to do admin work with my user already being in the admin group) but thats a minor thing

what is puzzling me and I am considering wiping it and starting again maybe trying the new beta is this

after a log in log out or reboot
my title bars for every program (firefox, any app, any window) disappear, then reappear. menus are still there but I can't top X out of an app

now I've seem to perm lost my network icon that let me select my wireless/wired network (that was default on install on ubuntu, my battery monitor icon, and such have just fell off the planet after one boot up so it has me scratching my head
I've managed using other app's get my wifi defaulted but I thought i'd dig before i wipe to help understand the flavour better and see whats going on

pc is a compaq nx7400 1 gig of ram 120 meg sata using 64 bit 8.04
gnome desktop with kde installed for apps

Robert

---

### Post by robert.corkum on 2008-10-18
anyone? am about 4 hours from wiping the box but would rather work long term to figure it out. did the same thing today, boot up no title bars any program, reboot they are back and still lost my network and battery icons and such full time

has me curious

---

### Post by buster2209 on 2008-10-31
This happened to me. I think it's a bug

I solved it like this;

ctrl + alt + F2.
This brings up the terminal.
Enter ur username and password.
Enter 'Gnome-panel' (minus quotation marks).
It will probaly tell you it isn't installed.
Enter 'sudo apt-get install gnome-panel' (minus quotation marks).
This will install the missing toolbar.
ctrl + alt + F7 will take you back to the desktop.

ctrl + alt + del and choose restart. IF this doesn't work, just unpluf ur PC

When your computer boots up, the bars should be back but some apps within the panel wont work - namely trash.

Go to 'Synaptics Package Manager' and install 'Gnome-desktop-data'

Restart

All should be good now.

This only happened to me once. Usually the first time you make theme changes and restart

Hope this helps

---


---
title: "Gnome Desktop Gone!"
date: 2008-02-22
forum: Desktop Environments
---

### Post by Macbeth417 on 2008-02-22
THE PROBLEM

My GNOME desktop is gone... all the side bars are gone. Ive tried restarting X and restarting the whole system. No luck

Any help would be much appreciated.

Events leading up to this:

My windows decoration manager was acting up this being Emerald. So i attempted to restart X with ctrl+atl+backspace. This reloaded emerald and compiz and solved the issue... however it did screw up my mouse as i have some imwheel stuff that loads at startup...  long story short machine froze when i tried to restart, I ended up having to hard restart.

Now i get the my regular splash login, i have right click-able nautilus options and i can access and my desktop background is accurate... additionally compiz loaded correctly and replaced window decorations with emerald... 

but... gnome desktop sidebars ect are all gone.

I spawned some  icons on the desktop for firefox and a terminal with the right click nautilus utils so im searching and testing things... any help would be appreciated

---

### Post by Macbeth417 on 2008-02-22
When issue gnome-session command 

it tells me gnome-session: you're already running a session manager

if i issue it after su to root i can load a root gnome session that has all of my side bars ect, however when i try to change back to my lower priv standard user it is all gone.

Anyone?

---

### Post by Macbeth417 on 2008-02-23
Very very odd. I was able to log in and change my session to Gnome. However when it loaded i could only see the background color, not even the desk top image. I used alt+ctrl+F1 to goto console then came back with alt+ctrl+F7 and gnome desktop apeared as normal... I then logged out... logged back in changing the session on log-in to Gnome and selecting it as the default and it seems to be working. All very strange.

---


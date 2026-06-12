---
title: "gnome x-windows bash problems"
date: 2005-04-22
forum: Desktop Environments
---

### Post by stepore on 2005-04-22
i just recently upgraded to hoary from warty. everything went fine in the upgrade, but i've had a few little problems. here's one:

gdm won't start on rebooting the computer or starting up from scratch (shut off). i actually have to sudo to root (sudo su) and /etc/init.d/gdm restart. then gdm and gnome will boot. but, that's not the real problem. the real problem is that when gnome finally boots up and i open a terminal and i do an echo $PATH, my path doesn't include nearly nowhere near the paths that i have when i do the 'echo $PATH' from a shell before i start x or gnome. or if i do a ctrl+alt+F2 to go to another terminal/shell i get all the $PATH that i should have.

exmaple. i've installed jre to /usr/local/java/ and from a terminal/shell (not started in x-windows) it shows up when i do 'echo $PATH'. but when i start gdm/gnome x-windows it doesn't show up in my path.

also, i can only get x-windows when i (as sudo) do /etc/init.d/gdm restart. once the pc boots up and i get a terminal window and i log in and try 'startx' it begins to start x but then it just shuts down. no error messages, nothing.

any help?

---

### Post by stepore on 2005-04-23
just a bit more to this. 

i've noticed that gnome or x-windows is ignoring my .bash_profile, but not my .bashrc or .bash_history. what gives? is this new to hoary?

---


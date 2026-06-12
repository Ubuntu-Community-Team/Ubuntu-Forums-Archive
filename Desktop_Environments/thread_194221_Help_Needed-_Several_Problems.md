---
title: "Help Needed- Several Problems"
date: 2006-06-11
forum: Desktop Environments
---

### Post by Hyakutaro on 2006-06-11
[FONT="Trebuchet MS"]Hello how's it going?

This is my first post here, the forums look nice so far :)
Anyway I have been using Ubuntu since v5.04, and I must say it's my favourite Linux Distro so far :D

Enough blablering, I have encoutered several problems with Ubuntu 6.06, maybe you could help me (bare with me I'm a n00b when it comes to Linux):

# [COLOR="Red"]My screen resolution is stuck at 1024x768, I would like to use 1280x1024 (just like in XP and Ubuntu 5.04/5.10)[/COLOR]

# I cannot seem to get my connection working, I open the Terminal and type **_sudo pppoeconf_** and follow the process, enter username and password, etc. However the connection is not working. (I also use a proxy if that matters)

# How can I edit the right-click menu, and add different shortcuts / fuctions?

[RIGHT]Thanks.[/RIGHT]

//Hyakutaro[/FONT]

EDIT: Fixed screen res problem ;)

---

### Post by ayoli on 2006-06-11
for the resolution a 
sudo dpkgreconfigure -phigh xserver-xorg
might do the trick.
Can't he for the connection, and the right click menu depnds of the app. I guess you mean right clik on desktop which s handled by nautilus. You can add things to right click menu in nautilus. One way is add scripts in $HOME/.gnome2/nautilus-scripts/
The other way is to use nautilus-tions extension which can be installed easy with:
sudo apt-get install nautilus-actions
cheers

---

### Post by glotz on 2006-06-11
How do you connect to net? DHCP or manual? (since you're havin problems with "pppoe", does you "e" work?)

---


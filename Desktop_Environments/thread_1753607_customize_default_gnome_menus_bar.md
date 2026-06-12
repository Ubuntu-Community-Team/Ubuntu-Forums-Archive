---
title: "customize default gnome menus bar"
date: 2011-05-09
forum: Desktop Environments
---

### Post by tjbradford on 2011-05-09
I have Searched and found a few pointers but not all thats required to solve my issue, 

I would like to edit my gnome menus bar so that it has 6 icons on it that point directly to different app's - the idea is that these settings are stored into /etc/skel so that each time a new user is created it will contain the custom apps on the bar that i added earlier

 cp -r /home/myusername/.gconfd /etc/skel
 cp -r /home/myusername/.gnome2 /etc/skel 

this works in as much if i remove the (menu Bar) panel from the menus bar then on new users being created that is cloned, great i thought i have sust it, but now adding the shortcut's to the bar and going through the same above process it is still a blank bar the icons are not shown. 

are the icon references stored somewhere else am i missing a directory that i need to copy ?

thanks

---

### Post by Krytarik on 2011-05-09
The custom menus/launchers are built up of the contents of these directories, maybe even more:
- "~/.config/menus": custom menu setup
- "~/.local/share/applications": custom launchers (not everything in that directory)
- "~/.local/share/desktop-directories": custom settings for submenus

Greetings.

---

### Post by tjbradford on 2011-05-09
this is so odd, if i create an iso of the source o/s using remastersys and include the above files it boots fine on a live vmware setup, however if i then burn that working iso to disc and boot a physical machine the system boots and the correct background is shown but the top and bottom menus are missing. 

what is different between the vm and the physical machines ?

---


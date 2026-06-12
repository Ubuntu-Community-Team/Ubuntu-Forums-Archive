---
title: "Ubuntu and KDE"
date: 2005-06-21
forum: Desktop Environments
---

### Post by mad_alfred on 2005-06-21
Hi,

i've recently installed the kubuntu package with synaptic ( I was using ubuntu with gnome before) and everything went fine: everytime i boot i log into kde and can start working perfectly, but when i log off the log on display of kde doesn't appear and i have to type username, password and then startx to start my desktop environment. Problem is that with the command startx gnome appears instead of kde so if i want to use kde i have to reboot!
Possible solutions?

thanks, for the help. :)

---

### Post by Dragonfly_X on 2005-06-21
Have a look at this thread, you should be able to find something there to fix your problem

[http://www.ubuntuforums.org/search.php?searchid=989810](http://www.ubuntuforums.org/search.php?searchid=989810)

---

### Post by mad_alfred on 2005-06-21
[QUOTE=Dragonfly_X]Have a look at this thread, you should be able to find something there to fix your problem

[http://www.ubuntuforums.org/search.php?searchid=989810](http://www.ubuntuforums.org/search.php?searchid=989810)[/QUOTE]
 well..i didn't find a solution to that :( except retuirning to gnome...

i'll look for a config file..there must be one that ubuntu uses to decide which desktop environment start when receiving the command startx, right?

:D

---

### Post by Dragonfly_X on 2005-06-21
[QUOTE=mad_alfred]well..i didn't find a solution to that :( except retuirning to gnome...

i'll look for a config file..there must be one that ubuntu uses to decide which desktop environment start when receiving the command startx, right?

:D[/QUOTE]

If you really want to use Kubuntu I would recommend a clean install, but personally I don't recommend Kubuntu although it is a great distro it's just not stable enough YET.

---

### Post by mad_alfred on 2005-06-21
[QUOTE=Dragonfly_X]If you really want to use Kubuntu I would recommend a clean install, but personally I don't recommend Kubuntu although it is a great distro it's just not stable enough YET.[/QUOTE]
 i agree!

by the way how do i uninstall kde?

---

### Post by mad_alfred on 2005-06-21
and what do you know?? i just switched to gdm with the dpkg reconfigure comand but kept kde as default desktop in the log on screen option dialog box!

magic! now it works!

---

### Post by Dragonfly_X on 2005-06-21
[QUOTE=mad_alfred]i agree!

by the way how do i uninstall kde?[/QUOTE]

If you want to uninstall KDE the best way is to issue the terminal command listed below. It will remove almost all of the applicable packages. What few packages remain can be removed with Synaptic by looking in the 'KDE Desktop Environment' section.

Code:

sudo apt-get remove kdelibs4 arts

---

### Post by Dragonfly_X on 2005-06-21
[QUOTE=mad_alfred]and what do you know?? i just switched to gdm with the dpkg reconfigure comand but kept kde as default desktop in the log on screen option dialog box!

magic! now it works![/QUOTE]

Cool! If you don't uninstall KDE I recommend u update to KDE 3.4.1 before u do anything else.

---

### Post by mad_alfred on 2005-06-21
[QUOTE=Dragonfly_X]If you want to uninstall KDE the best way is to issue the terminal command listed below. It will remove almost all of the applicable packages. What few packages remain can be removed with Synaptic by looking in the 'KDE Desktop Environment' section.

Code:

sudo apt-get remove kdelibs4 arts[/QUOTE]
 thanks m8! :D

---

### Post by Dragonfly_X on 2005-06-21
[QUOTE=mad_alfred]thanks m8! :D[/QUOTE]

Cool!

---

### Post by fdoving on 2005-06-24
For your information:

You can choose what to start when 'startx' is executed buy putting something in your ~/.xinitrc file.

Some exampels:

# This chooses to start KDE when startx is executed.

$ echo 'exec startkde' > ~/.xinitrc

# GNOME

$ echo 'exec gnome-session' > ~/.xinitrc

# Blackbox

$ echo 'exec blackbox' > ~/.xinitrc


.. and so on.

---


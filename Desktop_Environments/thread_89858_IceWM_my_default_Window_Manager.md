---
title: "IceWM my default Window Manager"
date: 2005-11-13
forum: Desktop Environments
---

### Post by Ruso on 2005-11-13
Hey all.

I run ubuntu 5.10 on my laptop wich is prity old machine PIII 800 with 256MB ram. And the GNOME works pritty slow. So I decided to use ICEWM insted. 
But I have no idea how to make Icewm my default window manager. But I want to start is automaticly on boot, how can I make it???

---

### Post by Hairy_Palms on 2005-11-13
before u login can u select icewm from gdm, then when you login from gdm you go straight into icewm.

---

### Post by veloct on 2005-11-13
[QUOTE=Hairy_Palms]before u login can u select icewm from gdm, then when you login from gdm you go straight into icewm.[/QUOTE]

Hairy is correct but just to clarify.  When you get to the log in screen, look for sessions and select icewm before you log in, once you enter your username and password it will ask you if you want to make it the default or just use it for one session, make it the default.  You're set then.

---

### Post by Ruso on 2005-11-13
The problem is that I dont have IceWM in the gdm menu. I do have xfce4 but not IceWM.

How can I make it manually?

---

### Post by az on 2005-11-13
[QUOTE=Ruso]The problem is that I dont have IceWM in the gdm menu. I do have xfce4 but not IceWM.

How can I make it manually?[/QUOTE]
How did you install icewm?  I just installed both the xfce4 and the icewm packages and they both appear in the gdm menu when I log in.

---

### Post by Ruso on 2005-11-13
> How did you install icewm?

Download IceWm from the internet

./configure
sudo make
sudo make install

and to run icewm i have to hit alt+ctr+F? login in non graphical mode and run this script:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#!/bin/bash
sudo echo Starting extra X server
sudo X :1.0&(exit)
DISPLAY=:1.0 icewmtray&(exit)
DISPLAY=:1.0 icewmbg&(exit)
DISPLAY=:1.0 icewm&(exit)

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

And I find this way pritty uncomfortable. :(

---

### Post by peanut butter on 2005-11-13
[QUOTE=Ruso]Download IceWm from the internet

./configure
sudo make
sudo make install

and to run icewm i have to hit alt+ctr+F? login in non graphical mode and run this script:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#!/bin/bash
sudo echo Starting extra X server
sudo X :1.0&(exit)
DISPLAY=:1.0 icewmtray&(exit)
DISPLAY=:1.0 icewmbg&(exit)
DISPLAY=:1.0 icewm&(exit)

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

And I find this way pritty uncomfortable. :([/QUOTE]

iwould just use the package

---

### Post by Ruso on 2005-11-13
Do you sugest me to reinstall IceWM using apt-get/synaptic??? 
I would prefer some other method less drastic, because I've configured IceWM into the way i like it!

---

### Post by super on 2005-11-14
just add a icewm.desktop file to /usr/share/xsessions
you can copy the contents of the file from anyone of the already existng .desktop file but change the 'exec=' line to 'exec=/usr/bin/icewm' and edit the name

---

### Post by Ruso on 2005-11-14
Thank you Super.

---

### Post by az on 2005-11-14
[QUOTE=Ruso]Do you sugest me to reinstall IceWM using apt-get/synaptic??? 
I would prefer some other method less drastic, because I've configured IceWM into the way i like it![/QUOTE]
The settings you have made are int /.icewm in your home directory, right?  That directory would not be touched by uninstalling the hand-made icewm and installing the icewm package from universe.

You have a much smaller chance of borking your system by using packages instead of making things from tarballs.

---


---
title: "Beryl problem"
date: 2007-06-01
forum: Desktop Effects &amp; Customization
---

### Post by neekz on 2007-06-01
I'm having a problem with beryl.  I was just customizing some of the effect and for some reason when I open something it doesn't appear to the forefront but behind anything that is currently open.  I want it to open like normal and appear in the forefront.  
  Did I change a setting by accident or is their some workaround I have to do. 

 Also how do I set beryl manager to open upon boot up??? 


 This is my first post and I would like to say I love Ubuntu! The best Distro I have had the pleasur to use.

---

### Post by youthforlinux on 2007-06-01
Alternatively, you can set up Beryl Manager to start up every time you log in:

GNOME

    * Go to System > Preferences > Sessions
    * Go to the Startup Programs tab
    * Click the Add button and type in beryl-manager
    * Repeat the previous step, adding beryl
    * Exit 

KDE

Simpler - but less graphical. In a terminal:

ln -s /usr/bin/beryl-manager ~/.kde/Autostart/beryl-manager

In case you have trouble starting up after adding beryl-manager to the Session startup (such as getting the White Cube/blank screen after the Beryl logo), and hence can't get to the GUI to remove them, you can do the following to remove it:

Press Ctrl-Alt-F2 to get to a console, log in, and type:

Gnome:

rm ~/.config/autostart/beryl-manager.desktop


KDE:

rm ~/.kde/Autostart/beryl-manager

Now you should be able to log back in by either pressing Ctrl-Alt-F7 (to get back to the display) followed by Ctrl-Alt-Backspace (to restart the X server), or by typing sudo /etc/init.d/gdm restart (kdm start for KDE) in the terminal followed by Ctrl-Alt-F7.
[edit]
Using Beryl

If you find it too slow then open up Beryl Settings Manager and remove (or tweak) the blur effect -- some combinations of settings are really slow on some graphics cards.

---

### Post by neekz on 2007-06-01
0_0 it is just that easy!! 

 I'm loving it, thanks I just set it up and the whole new app thing was fixed when I switched rendering platform to "force nvidia". 
 
  Thanks for the help :)

---


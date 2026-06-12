---
title: "login problem"
date: 2008-03-17
forum: Desktop Environments
---

### Post by cybernet on 2008-03-17
when i login it shows me a black blank screen with cursor
what i have to do ?

what is wrong :confused:

---

### Post by ajgreeny on 2008-03-17
Assuming you haven't just installed a server version, login with your username and password (password will not show on screen but don't worry about that). Now type startx and see if anything happens.
If no success, type ```
sudo dpkg-reconfigure xserver-xorg
``` and enter your password.  Use the tab and cursor buttons to move the cursor or go to the OK and spacebar to select resolutions, etc. and answer the questions as best you can.  If you don't know the answer, accept what is showing.  When you get to the graphics section chose the driver best suited for your graphics card, eg nv for an Nvidia or ati for an ATI card.  When you get to the end reboot, and with luck you may get into gnome.  If not go through the xserver thing again but chose vesa for the driver which should give you a GUI of some sort from which you can try to get the proper driver (proprietary?) installed and running by using the System>Administration>Restricted Drivers Manager from the menus.
Good luck!

---

### Post by cybernet on 2008-03-17
the login windows shows after i write the user and password nornaly it should see desktop but instead i've got a a black blank screen the cursor i can move it



thanks for the fast answer and for detailed answer

now i have to test it :)


thanks a lot

cybernet :popcorn:

---

### Post by cybernet on 2008-03-17
after i boot the windows everything worked perfectly

i swear it god i didn;t do anything on windows that should affect ubuntu

but thanks anyway :popcorn:

---


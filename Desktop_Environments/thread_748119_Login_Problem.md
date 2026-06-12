---
title: "Login Problem"
date: 2008-04-07
forum: Desktop Environments
---

### Post by caesarcardinale on 2008-04-07
I think this is the right forum for this, so here goes.

I'm having a problem logging to my regular xclient/gnome session.  I get to the login page as usual, enter my username and password.  Then it goes to a screen that's background color (ubuntu default sort of tan/orange) and then it shoots me back to my login screen.  There are no error messages or anything.  I'm currently logged into failsafe gnome.  I was screwing around with my ATI graphics card stuff yesterday (trying to get direct rending to work for Freespace2), that might have something to do with it.  Can any of youse help me?

---

### Post by ajgreeny on 2008-04-07
O presume you have messed up your graphics driver so I would try ```
sudo dpkg-reconfigure xserver-xorg
``` and when you get to the driver section chose then ati driver.  Reboot or at least restart x with ctrl+alt+backspace and hopefully you will now have a GUI appear.  You can then see later if there is a proprietary driver available for your card in the Restricted Drivers Manager of the menus.

---


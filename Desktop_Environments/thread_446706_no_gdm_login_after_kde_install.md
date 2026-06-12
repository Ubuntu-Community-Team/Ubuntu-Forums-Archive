---
title: "no gdm login after kde install"
date: 2007-05-17
forum: Desktop Environments
---

### Post by bjb1959 on 2007-05-17
Help.... I installed Ubuntu 7.04 and had everything humming along just fine.  Then I installed the kde environment using synaptic and can get the KDM login to work if I change to that as the default display manager. I uninstalled kdm and re-installed gdm but it still doesn't work. I have my system set to auto boot into GNOME so I can get to my desktop but if I logout I just get a screen flicker a couple of times and then the spinning mouse until I kill the session with ctl F1 and then reboot.  Any ideas what happened and how to fix it??  :confused:

---

### Post by Kuoi on 2007-06-15
Found this in an other threath , and this worked for me :
--------------------------------

1) Open a terminal session by pressing Ctrl+Alt+F2 and login with your username and password. Make sure you have administrative rights or login with a username that does.
(You can go back to the graphical environment by pressing Ctrl+Alt+F2

2) Type following:
> sudo dpkg-reconfigure kdm

and select gdm as your display manager

3) Restart the system. 
------------------------------------

Hope this helps , Kuoi

---


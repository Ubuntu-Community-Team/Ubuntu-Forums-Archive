---
title: "login and start gnome from terminal"
date: 2005-08-10
forum: Desktop Environments
---

### Post by cazz on 2005-08-10
Can I login and start gnome from a terminal?

---

### Post by varunus on 2005-08-10
If you mean log in without a GUI at all and then start gnome, yes; just type "startx" into the prompt.  You need to do the following:
```
sudo update-rc.d -f gdm remove
```
This will stop X windows from starting.  You'll log into a console, if you want X, just type startx.

If you mean log in with a GUI but start GNOME later, that is also possible.  Just log into the "failsafe Xterm" from the Sessions menu in the login screen, and type "gnome-session&" to start GNOME.  Unfortunately if you do this you can't close the terminal or GNOME will quit and you'll log out.  Someone may know how to do this better.

---

### Post by cazz on 2005-08-10
ok but I mean if I have restart linux whit a terminal and like to login whit terminal so VNC start running?

---

### Post by varunus on 2005-08-10
Um, could you clarify the above? Do you mean you want to be able to reboot from GNOME into just a terminal?  And then start VNC?

---

### Post by cazz on 2005-08-10
I mean like this

I'm at work and I use VNC to work a little with my Ubuntu at home
And if I need to reboot my Unbutu I use "shotdown..."
When the reboot is finnish I can login whit terminal but not with VNC because (I only guess now) Gnome is not running.
I need to go home and login with a username and a password to Gnome to start and then I can use VNC.

---

### Post by varunus on 2005-08-10
Ohhhh, I see.

well, the way to start GNOME would be to issue the "startx" command in your text console to your home computer, then try VNC'ing in.  It might work.  I don't know though.

You can also set up the Login Screen to log in a user automatically; just go System->Administration->Login Screen Setup.  The log in a user automatically after XX seconds is an option there, if you're not worried about someone else at home using your computer, its the best way.

---


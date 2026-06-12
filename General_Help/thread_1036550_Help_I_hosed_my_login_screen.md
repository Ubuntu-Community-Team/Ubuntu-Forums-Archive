---
title: "Help: I hosed my login screen"
date: 2009-01-10
forum: General Help
---

### Post by iJava on 2009-01-10
I'm a newb and a dope, I was poking around my new Ubuntu 8.10 install (which rocks) poking around seeing what does what...

I was in Administrator >> Login Screen and I selected "chooser" instead of "greeter". Now when I boot, instead of a login screen I'm presented with a box asking me to add a server and connect to it?

I tried entering both "localhost" and "127.0.0.1" but it could not find either.

NOW WHAT?!?

Thanks guys.

---

### Post by Denestria on 2009-01-11
Ctrl+Alt+F1 to get to a terminal, login and
```
sudo nano /etc/gdm/gdm.conf
```

Search for this section:

[xdmcp]
# Distributions: Ship with this off.  It is never a safe thing to leave out on
# the net.  Setting up /etc/hosts.allow and /etc/hosts.deny to only allow local
# access is another alternative but not the safest.  Firewalling port 177 is
# the safest if you wish to have xdmcp on.  Read the manual for more notes on
# the security of XDMCP.
Enable=true

Edit enable to = false, save it.
```
sudo /etc/init.d/gdm restart
```

Logout, ctrl+alt+F7 (or F9) to get back to graphical login.  I think that does it.

---

### Post by sheffel on 2009-02-04
I experienced the same problem, symptoms, and cause, which I'll redescribe:

The Ubuntu (8.10 Intrepid Ibex) gdm Greeter login menu has been replaced with the Chooser (XDMCP) menu, thereby disabling login to the localhost. This was caused by configuring (from Gnome) as follows:

1) From the "System" menu, select "Administration"->"Login Window" which brings up the "Login Window Preferences" window.
2) Select the "Security" tab, then click the "Configure X Server..." button brings up the "X Server Login Window Preferences" window.
3) Under "Server Settings" change the "Launch:" parameter from "Greeter" to "Chooser".

Root Cause: Apparently, this sets a parameter in the /etc/gdm/gdm.conf-custom file:
chooser=true

Solution: Edit the /etc/gdm/gdm.conf-custom file and set:
chooser=false

Most of the solution that the previous poster provided is useful:

) Ctrl+Alt+F1 to get to a terminal, login, and edit:
# sudo nano /etc/gdm/gdm.conf-custom      # Edit with nano or vi

) Set chooser parameter to false:
chooser=false

) Restart gdm or reboot the server:
# sudo /etc/init.d/gdm restart         # Restart gdm or reboot

) If you restarted gdm, then logout (ctrl+alt+F7 or F9) to get back to graphical login.

This reverted gdm back to the Greeter and enabled logins.
Jeff Sheffel

---

### Post by jpeddicord on 2009-02-05
This thread or post has been moved from the Desktop Effects & Customization forum as the posted content is considered off-topic.

Desktop Effects & Customization is a forum for discussing:
[LIST]
[*]Compositing managers such as Compiz
[*]Themes (window themes, widget themes, backgrounds, etc)
[*]Appearance preferences
[/LIST]
Your post did not fit any of these categories, so it has been moved.

Common types of off-topic threads include:
[LIST]
[*]GNOME/KDE/XFCE help in general
[*]Hardware problems not directly related to compositing
[/LIST]

Thanks,
Jacob

---


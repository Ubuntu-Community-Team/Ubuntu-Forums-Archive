---
title: "Autostart network-manager in LXDE"
date: 2009-03-07
forum: Desktop Environments
---

### Post by Steve1961 on 2009-03-07
The title says it all really.  I'm playing around with LXDE at the moment and haven't been able to find a way to autostart network-manager.  I can start it fine by the command line but there must be a way to add it to the LXDE session.  Anyone know how?

---

### Post by KhaaL on 2009-04-22
I agree with you here. its quite stupid to not being able to connect to a wifi because nm-applet is not autostarted.

---

### Post by bchapman on 2009-05-03
You need to copy the nm-applet.destkop file into the appropriate directory. Try something like this:

```

$ if [ ! -d ~/.config/autostart ];then mkdir ~/.config/autostart; fi
$ cp /etc/xdg/autostart/nm-applet.desktop ~/.config/autostart/

```

Log out and log back in. This appeared to work for me on 8.10. It appears that LXDE does not pay attention to system-wide /etc/xdg/autostart/ files.

[http://wiki.lxde.org/en/LXSession](http://wiki.lxde.org/en/LXSession) has more information, including a note about some desktop files that will only start under Gnome. My nm-applet.desktop did not have that issue.

Best regards,

Ben

---

### Post by keithpeter on 2009-05-04
> **bchapman said:**
> You need to copy the nm-applet.destkop file into the appropriate directory. Try something like this:

```

$ if [ ! -d ~/.config/autostart ];then mkdir ~/.config/autostart; fi
$ cp /etc/xdg/autostart/nm-applet.desktop ~/.config/autostart/

```

Log out and log back in. This appeared to work for me on 8.10. It appears that LXDE does not pay attention to system-wide /etc/xdg/autostart/ files.

[http://wiki.lxde.org/en/LXSession](http://wiki.lxde.org/en/LXSession) has more information, including a note about some desktop files that will only start under Gnome. My nm-applet.desktop did not have that issue.

Best regards,

Ben

Hello Ben and all

This worked using LXDE on top of a 9.04 Jaunty XUBUNTU install with one modification. I had to open the autostart file and add LXDE to the list of window managers that the nm-applet loads under as below, see the OnlyShowIn line

```

[Desktop Entry]
Name=Network Manager
Comment=Control your network connections
Icon=nm-device-wireless
Exec=nm-applet --sm-disable
Terminal=false
Type=Application
OnlyShowIn=GNOME;XFCE;LXDE
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=NetworkManager
X-GNOME-Bugzilla-Component=general
X-GNOME-Autostart-enabled=true
X-Ubuntu-Gettext-Domain=nm-applet

```

Thanks very much.

---

### Post by the dsc on 2009-07-18
For me it didn't work, for some reason. Funny how something that is supposed to be more user friendly (LXDE, compared with pure openbox) can have such issue. 

I also tried to create an autostart.sh on openbox' directory, with exec ~/.config/autostart/nm-applet, to no avail.  :?

Extremely annoying.

Executing the very same .desktop will work after I'm on LXDE, even by command line, but it's simply ignored as something that has to start automatically.



I've just added another random .desktop (gedit) to see what happens, and oddly enough, it auto-starts.

---

### Post by the dsc on 2009-07-18
Solved. Found the solution on Arch Linux forums, even though I'm using ubuntu. Here it goes, just in case someone would also be scratching his head at the point of reaching to the bone:

> ok the "problem" is solved, normman, i've checked the link that you gave me but i don't have the autostart file in the direction that wiki said. So, i use the archwiki [http://wiki.archlinux.org/index.php/LXD](http://wiki.archlinux.org/index.php/LXD) &#8230; t_Programs , all that we (lxde users) must do is to put the name of the program that we want to start with the system in /etc/xdg/lxsession/LXDE/autostart


[http://bbs.archlinux.org/viewtopic.php?id=74309](http://bbs.archlinux.org/viewtopic.php?id=74309)


---


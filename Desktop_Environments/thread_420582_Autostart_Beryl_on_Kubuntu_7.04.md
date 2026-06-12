---
title: "Autostart Beryl on Kubuntu 7.04"
date: 2007-04-23
forum: Desktop Environments
---

### Post by verevi on 2007-04-23
Beryl is nice and easy and working great on Beryl for me.  But I have two questions:

1) What is the best way to have it start when my session starts?  If I put it in .kde/Autostart/startberyl.sh, it starts but uses the kwin stuff.  I have to choose beryl after that.

2) When I do load Beryl, the "Adept Notifier" green circle shows up on the top left corner of my screen.  ???  I'd love for that to go away.  

Thanks for the help!

---

### Post by sharke on 2007-04-23
To start beryl at login goto>System>Preferences>Sessions>new Name= Beryl Command=beryl-manager click okay close and your done beryl should now start after login.
Regards
Sharke

---

### Post by verevi on 2007-04-23
Thanks, but that works for Gnome, but how about for KDE?

> **sharke said:**
> To start beryl at login goto>System>Preferences>Sessions>new Name= Beryl Command=beryl-manager click okay close and your done beryl should now start after login.
Regards
Sharke

---

### Post by sharke on 2007-04-23
kde from memory you should have a folder called auto start in your home directory try adding beryl-manager to it.
Regards
Sharke

---

### Post by SebbeJohan on 2007-04-28
I'm installing Beryl now on my laptop and this is the autostart proposed for Kubuntu in this Howto [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_AIGLX]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_AIGLX")

"To create the session shell script, open up your favourite text editor (eg gedit or kedit) as Root and create a new script named startberyl.sh: 
```
gksudo gedit /usr/bin/startberyl.sh
```

For KDE, use kdesu instead of gksudo

[B]#!/bin/sh
 export KDEWM="/usr/bin/beryl-manager"
 exec startkde[/B]

Now you need to make the script executable; this can be done in Nautilus or Konqueror (running as Root) by right-clicking the file and choosing Properties, or in the terminal: 
```
sudo chmod a+x /usr/bin/startberyl.sh
```

To create the session, create the file /usr/share/xsessions/Beryl.desktop, and give it the following contents in a text editor (again, as root or using gksudo/kdesu): 
```
gksudo gedit /usr/share/xsessions/Beryl.desktop
```

[B][Desktop Entry]
Encoding=UTF-8
Name=Beryl
Exec=/usr/bin/startberyl.sh
Icon=
Type=Application[/B]

Now when GDM or KDM starts, you should have a session called Beryl available for selection; if you log into this session, Beryl will run (via the startberyl.sh script) and load GNOME or KDE for you. Logging into your normal session will give you a standard, un-accelerated desktop for troubleshooting or running programs which don't play nicely with AIGLX."

ET voila, hope it helps!
regarding the bug with Adept, I have the same problem... but no solution... I saw that the bug was reported... have to wait:KS

---

### Post by jollemeyer on 2007-08-01
OK, that also worked for me. Beryl starts up fine when I log into Kubuntu 7.04.

However, I do use the cube under beryl and allocated some windows onto the different edges.
How do I manage to re-allocate the windows onto these edges on startup?

When beryl starts up, all windows are cluttered on a single edge of my cube.

I don't want to move all the windows over and over once I re-login.

Please help.

---

### Post by jollemeyer on 2007-08-07
Hey you !!

do you know how I can make Beryl to allocate my applications on the different sides of my cube automatically once I re-start my kubuntu 7.04?

I have to move all apps to a certain side of the cube by hand.

When I restart my system, all applications are on a single side of the cube and I have to move them again.

Please help.

---


---
title: "Beryl with ATI 1600, fglrx"
date: 2007-04-08
forum: Desktop Effects &amp; Customization
---

### Post by Petar Marjanovic on 2007-04-08
I want to install Beryl on my PC. This are my fglrx informations:

petar@petar-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series Generic
OpenGL version string: 2.0.5814 (8.25.18)

Does this card support berrly? Otherwise: Does beryl support this card?

---

### Post by mcduck on 2007-04-08
Yes, it works great. You just need to use fglrx & XGL, AIGLX and open drivers don't work too well with X1600.

---

### Post by Petar Marjanovic on 2007-04-08
Is there a tutorial for newbies like me?

---

### Post by danhm on 2007-04-08
There is!

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu)

Remember, you want XGL, as ATI drivers and AIGLX don't play nice together.

---

### Post by Petar Marjanovic on 2007-04-08
Is there an other program like Beryl or Compiz to modif one's Desktop? I don't really want to crash my system again.

---

### Post by philipho on 2007-04-09
I am using mobility radeon x1600. i followed this guide: [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

---

### Post by GhOstRiDerSiX on 2007-04-09
You can try this tutorial: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL)
I have a x1600xt on my PC and it works great with beryl :)

---

### Post by Petar Marjanovic on 2007-04-12
Thank you both. But, if i want to activate a theme:

> petar@petar-desktop:~$
 **************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension


---

### Post by Petar Marjanovic on 2007-04-12
Oh, me is a stupid boy. I have to start Ubuntu in xgl mode. 
It works, but when i start beryl-manager, I see just gray.

petar@petar-desktop:~$ beryl
**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.2)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0
petar@petar-desktop:~$

---

### Post by ak2007 on 2007-04-15
I had the same problem and solved it by doing this:

**Changing your standard login**

For GNOME: Instead of adding a beryl-parate desktop session, you could alter your standard X session. This is not recommended for most users.  It might be useful however if you do not want to set up a separate X session for Beryl for some reason.

First change gdm.conf-custom:

$ sudo nano /etc/gdm/gdm.conf-custom

Go to the very bottom of the file and add:

0=Xgl
[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true

When you reboot or restart the graphical session, the Xgl server should be running.

**Running Beryl**

Now it's time to test your Beryl installation. Open a terminal and type

$ beryl-manager

If all goes well, you should see the Beryl splash screen and your windows will become wobbly! Your system tray should show the Beryl icon - a red gem - that you can use to adjust beryl's and emerald's settings. Click on 'Beryl settings manager' or Emerald, the theme manager. It also provides fallback to another window manager (metacity for example), in case Beryl crashes.

If you don't see the beryl splash screen immediately, you may need to tell the manager to load Beryl - right-click on the red gem, go to "Select Window Manager" and choose "Beryl". If that doesn't work, there's a problem somewhere! Often, useful debugging output will show in the terminal window you used to start beryl with.

---


---
title: "OAFIID Gnone panel crashes"
date: 2011-01-16
forum: Desktop Environments
---

### Post by Jim_Hope on 2011-01-16
OAFIID Gnone panel crashes

Since I upgraded to Ubuntu 10.10, my computer spends 5+ minutes starting up. Of that, 2 minutes or so are spent getting to log-in, which is longer than Ubuntu 10.04 took. After I log-in, it takes up to 5 minutes just to load up.

I am not entirely sure what is causing this. Almost every time I start up, all the panel applets crash (e.g. "The panel encountered a problem while loading "OAFIID:GNOME_ShowDesktopApplet").

The panels that reliably fail to load are: the clock, indicator applet, indicator applet session, and fast_user_switch, though the latter is not an applet I have added to the panel.

Deleting and reloading the applets, changing their location etc. does not change the problem.

I know this problem has been much commented on in the forums. I have tried all the following solutions:

-- Resizing the panel
--sudo [COLOR=#3465a4]/etc/init.d/gdm[/COLOR] stop
sudo aptitude reinstall gnome-applets
-- sudo apt-get install indicator-applet-session
(its already installed)
-- reinstalling: gnome-panel/gnome-applets/gnome
 &#8211; Reinstalled libsoup2.4-1.

Does anyone have any other suggestions? I have made a pretty thorough search of the forums without finding a solution. Any help would be gratefully appreciated.

cheers,

Jim

---

### Post by Jim_Hope on 2011-01-22
Dear All,

I have found the relevant error in .xsessions: 

** (gnome-panel:2842): WARNING **: panel-applet-frame.c:1310: failed to get Bonobo/Control interface on applet OAFIID:GNOME_IndicatorApplet:
Unknown CORBA exception id: 'IDL:omg.org/CORBA/COMM_FAILURE:1.0'

This error repeats for all the panel applets. I have searched the forums and the internet, but this error message only tends to come up in bug reports - does anyone have any ideas?

cheers,

Jim

---

### Post by steelsteel! on 2011-01-29
Hello! Im under Ubuntu 10.04 on an imac19' Every time after login fastuserswitch applet crashes:  panel-applet-frame.c:1273: failed to load applet OAFIID:GNOME_FastUserSwitchApplet: (null)

---

### Post by Jim_Hope on 2011-02-10
Can anyone help me with this? I have been through the forums again and am at my wits end.

cheers,

Jim.

---

### Post by Jim_Hope on 2011-02-14
Bump.

---


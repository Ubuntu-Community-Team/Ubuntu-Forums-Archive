---
title: "New Karmic gdm side-effects"
date: 2009-10-30
forum: Desktop Environments
---

### Post by jeffus_il on 2009-10-30
The new Karmic gdm cancels my virtual desktops in openbox.
It also cancels the xorg keyboard layout switching defined in hal

I switch to xdm and all works fine (no other changes)

Any ideas?

---

### Post by bkann on 2009-11-05
If you used any special trickery, would you mind sharing how you got the Openbox desktops to work with XDM?

When I lost my virtual desktops at upgrade, the first thing I did was to go back to XDM.  It seems that no matter how I configure it, it only works as a simple Openbox session or a full Gnome session.  I have not been able to invoke the Gnome/Openbox combo from either GDM or XDM.

I have, however, found that if I use OBConf to adjust the number of desktops down and then back up, they all come back until the next reboot.  It's frustrating, but it works.

---

### Post by jeffus_il on 2009-11-07
No trickery, I'm not a politician;)
I am running regular Openbox, not Gnome/Openbox
Check the .xsession-errors file in your home directory for the Gnome/Openbox error.
I run Openbox with tint2 and wbar.
Maybe it's best to delete the .xsession-errors file before your attempt to make it smaller and more understandable.
You could of course change your window manager in the gnome session to Openbox, I think using gconf-editor.

By the way, I believe the root of the problem is that the new gdm runs on an X Server whereas xdm only runs an X Server when you login. So once you get into openbox from gdm, the X Server is already set up for one virtual desktop, that's why you can change it in obconf, but it will not be there in the next session. I don't like these design decisions by Ubuntu, but I suppose it is necessary for marketing, less tweaking more Gui.

---


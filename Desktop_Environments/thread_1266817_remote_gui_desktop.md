---
title: "remote gui desktop?"
date: 2009-09-15
forum: Desktop Environments
---

### Post by chitowner2 on 2009-09-15
Hello Fellow Geeks!

OK, I finally got my new media box running. I set aside the Buffalo wireless-N and got one from Rosewill. Set it up on the new box using knetworkmanager. (not a great app, but not my topic now) and got my viewsonic 30-inch connected via DVI, so the system is working nominally now.

So- here's the current issue I am seeking direction on: 

I would like to have a full gui control of the new box (jaunty/kde4.2) remoted via the wireless-N to my good ol' desktop (jaunty/kde3.5) which is connected to the shared router by cable. The router has been flashed with DD-WRT.

Any URL's or instruction as to how to do this will be greatfully received.
CT

---

### Post by lian1238 on 2009-09-15
Remote desktop? In ubuntu, i enable remote desktop for the server in System,Preferences,Remote Desktop. For the client, I use vinagre or vncviewer.

Is this what you're looking for? If you don't have this in kde.. try looking for vnc.

---

### Post by chitowner2 on 2009-09-15
kde 4.2 seems to have something called "Krfb" which directs one to use VNC. I am familiar with VNC, but it does not install with apt-get on kde 3.5. Both OS's are Jaunty.

I ran synaptic and found several variants of VNC available. The gnome version, vinagre does not give me a usable connection- just a black screen. 

I tried x11vnc and got a bunch of stuff about password. Krfb provides one, and I assume it would be different for each session but x11vnc wants to store a static password. Maybe there is a way to open x11vnc from C/L with a string that specifies password?

I tried TSclient but it needs a domain name. Color me stupid, but I did not establish a domain name on my router. 

I tried to use gvncviewer too, but that needs command line options that I do not understand how to use. 

So I am at a dead end here. I just don't know enough to dope my way through the issues to get one of these to work.

:confused:

---

### Post by StuartN on 2009-09-15
> **chitowner2 said:**
> I would like to have a full gui control of the new box (jaunty/kde4.2) remoted via the wireless-N

You could use "ssh -X the_new_box" which will open a remote terminal CLI on the new box, but with X-forwarding. Then "Nautilus" etc will open almost any GUI application remotely. You need to install the ssh server daemon on the new box, as only the client is installed by default. My experience is that ssh -X is much faster and more responsive than vnc.

---

### Post by krunge on 2009-09-15
> **chitowner2 said:**
> Maybe there is a way to open x11vnc from C/L with a string that specifies password?

x11vnc does not require a password it is just warning you that you are not using one.

Since you are connecting over your LAN, maybe you don't feel you need a password. But if you want to, the easiest way to supply one is```
x11vnc -passwd mysecret
```there are also ways to specify a password stored in a file.

BTW, to avoid an Xorg bug, I suggest adding the "-noxdamage" option, e.g.:```
x11vnc -passwd mysecret -noxdamage
```

---

### Post by chitowner2 on 2009-09-15
> **StuartN said:**
> You could use "ssh -X the_new_box" which will open a remote terminal CLI on the new box, but with X-forwarding. Then "Nautilus" etc will open almost any GUI application remotely. You need to install the ssh server daemon on the new box, as only the client is installed by default. My experience is that ssh -X is much faster and more responsive than vnc.

Hey, that's pretty slick!
It actually works well for me, since nautilus is good at displaying icons of multi-media files and that's pretty much what my new box is for. 

Thanks!

---

### Post by chitowner2 on 2009-09-15
I am also trying out "fish" in konqueror. that allows me to do file transfers that a remote copy of nautilus does not. between the two of them I get most of the functions I want. Not as "pretty" as what I was looking for, but easy and functional. <g>

refinement of the nautilus trick: open the "location" window above the nautilus file display ('letter icon' thingie) and type "ssh://some_other_PC". Now open another nautilus window for local_machine (for ease of use) and you can swap files in a gui environment as well as have the better icon rendering of nautilus.

CT

---


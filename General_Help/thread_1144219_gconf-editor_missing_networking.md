---
title: "gconf-editor missing networking"
date: 2009-04-30
forum: General Help
---

### Post by shanev on 2009-04-30
I'm running Ubuntu 9.04.

I'm having trouble getting a pptp vpn connection to a Windows server and all the posts I can find recommend running gconf-editor and under /system/networking changing some settings.  I don't have/can't find "networking" under anything in gconf-editor.  If I search for "network" it only comes up with 2 keys related to evolution.

Can someone tell me what I'm missing or help me get the /system/networking section back in gconf-editor?

[IMG]http://i575.photobucket.com/albums/ss192/shanevanhulle/Screenshot-ConfigurationEditor-syst.png[/IMG]

Thanks!!

---

### Post by jpseixas on 2009-05-07
You probably set the option to make the connection available to all users. Since the gconf-editor is a per-user configuration, you cannot edit connections that are available to all users.

To test it, uncheck the "make this connection available to all users" at the configuration panel of the VPN connection you created (or something like that, my Ubuntu is in another language), and see if you get the "networking" back to the gconf-editor.

Don't ask me how to use the gconf-editor to edit a connection that is available to all users, since I'm still trying to find that out...

---


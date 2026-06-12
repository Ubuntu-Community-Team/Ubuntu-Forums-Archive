---
title: "nm-applet in kde"
date: 2009-08-09
forum: Desktop Environments
---

### Post by KhaaL on 2009-08-09
Hi

Since KDE's version of network manager dosent seem to have support for PPTP vpn's, and kvpnc can't disconnect from a VPN once disconnected, I'm forced to use the ordinary nm-applet from gnome. but when I try that, this is the output i get

khaal@Xeraphim:~$ nm-applet 

** (nm-applet:16475): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3



How can I find out what service that is being used in its place?

---

### Post by Raboch on 2009-08-09
Try removing the network manager plasmoid or quitting knetworkmanager and then launch nm-applet. If that works then you can add nm-applet to start when you log in (system settings, advanced, autostart, add script).

---

### Post by KhaaL on 2009-08-09
> **Raboch said:**
> Try removing the network manager plasmoid or quitting knetworkmanager and then launch nm-applet. If that works then you can add nm-applet to start when you log in (system settings, advanced, autostart, add script).

That didnt help, i removed nm widget and i still cant start it:

(Reading database ... 246927 files and directories currently installed.)
Removing plasma-widget-network-manager ...
khaal@Xeraphim:~$ nm-applet 

** (nm-applet:4324): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3

---

### Post by JasenGroves on 2009-08-09
Try this

nm-applet --sm-disable

I've used that in KDE successfully without any troubles.

---

### Post by KhaaL on 2009-08-09
khaal@Xeraphim:~$ nm-applet --sm-disable

** (nm-applet:11084): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


that was after the reinstallation of nm...

---


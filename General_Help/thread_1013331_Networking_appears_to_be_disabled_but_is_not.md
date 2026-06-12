---
title: "Networking appears to be disabled but is not"
date: 2008-12-16
forum: General Help
---

### Post by PaulWhipp on 2008-12-16
After updating 15/12/08 in ubuntu 8.10 my network cards disappeared from the Network connections gui and my network reported as disabled (and indeed was).

Following some chatting and research I added:
auto eth1
iface eth1 inet dhcp

to /etc/network/interfaces

and restarted the network.
Everything now works fine but the network connections gui still has the warning triangle and tells me that the networking is disabled.

A minor irritation but does anyone know how to fix it?

---

### Post by benhewson on 2008-12-18
I have had similar problems with kubuntu after an update of network manager.

I had a static IP address set and had configured a vpn connection.
After the update none of it worked. I have since created a new static address which does work, however I have had no luck at all with the vpn connection. It just refuses to connect.

---

### Post by PaulWhipp on 2008-12-18
I'm wondering if the best thing to do will be to remove and then re-install network-manager-gnome and network-manager.

I'm nervous about losing the network in the process though and I've got everything working at the moment - its just the network manager displaying incorrectly that the network is disabled.

---

### Post by cormic on 2008-12-23
I have the exact same issue.

---

### Post by PaulWhipp on 2008-12-23
I've switched the network manager and its icon off in the preferences/Sessions list by un-checking the network manager box so at least there is no misinformation on my screen.

I don't want to uninstall it until I understand what is happening.

I tried manually running the start command:
sudo nm-applet --sm-disable

and got
** (nm-applet:6559): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:6559): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

[there is no man entry for this command which is v. bad for a supported command]

The errors seem to imply that the network is being served by another network service (the one that is now working for us). I can't see any obvious way to access or configure that though but perhaps an update has turned it on which has caused this problem.

Hopefully someone who knows about the networking side of Ubuntu will read this and set us to rights, otherwise I'll bumble on and see if I can find out more when I get some time. In the meantime my system works - its just an irritation not being able to see the network status at a glance.

---


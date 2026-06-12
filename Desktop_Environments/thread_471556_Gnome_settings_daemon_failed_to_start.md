---
title: "Gnome settings daemon failed to start"
date: 2007-06-12
forum: Desktop Environments
---

### Post by piyush_srivastava on 2007-06-12
I have Edgy (6.10) on an IBM r52 Thinkpad (Intel Celeron ).

The Gnome session has suddenly started to take a long time to log in, although KDE works fine. Even when Gnome logs, in it displays a warning that The GNOME settings daemon could not be started. The theme settings also do not work properly in tis condition.

I tried creating a different user account but that did not help.

Thanks in advance.

Piyush.

---

### Post by piyush_srivastava on 2007-06-12
Here s the output that I get when I try running gnome-settings-daemon from a terminal:

(gnome-settings-daemon:10299): GSwitchIt-WARNING **: Unable to connect to dbus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

** (gnome-settings-daemon:10299): CRITICAL **: dbus_g_connection_register_g_object: assertion `connection != NULL' failed

** (gnome-settings-daemon:10299): CRITICAL **: dbus_g_proxy_new_for_name: assertion `connection != NULL' failed

** (gnome-settings-daemon:10299): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed
GTK Panel of SCIM 1.4.4

After this a bug is reported by bug-buddy.

Thanks

---

### Post by piyush_srivastava on 2007-06-13
Hello,

I solved the problem finally.
It had probably to do with the fact that NetworkManager can sometime shut down the loopback interface.
When I replaced the contents of the /etc/network/interfaces with  the backup file that Ihad created when I cleared the above file for making NM work, gnome settings daemon started working.
I have seen that I can reproduce the problem also by repeating the above sequence of steps.


I would like to get a more precise description of the problem and the solution, since it appears to me that it has to do with how the library dbus works.

Thanks.

---

### Post by pepsi_max2k on 2007-06-23
i have a strange feeling this may be the same reason i can't get my desktop loaded depending on whether i have an ethernet cable connected or not / when i do have daemon startup, password box,various other errors / no loopback for webserver.

i don't think i have a backup of /etc/network/interfaces  though, how could i go about checking what's wrong with / fixing it?

**EDIT:**

/etc/network/interfaces contains:

> iface eth0 inet dhcp




auto eth0

does seem a little... erm.... sparse?


**EDIT:** deffinately sounds like same problem, i have no loopback iface either :(

**EDIT 3:**

Changing /etc/network/interfaces to the following seemed to have fixed stuff up:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

---

### Post by Xcalibur99 on 2007-09-11
I had the samme problems. Login took forever and ended up with Gnome settings manager failing to start. Both my hosts and interfaces files seemed ok, but commenting out all entries with IPv6 in /etc/hosts solved my problems.

---


---
title: "Shutdown Problem in 8.04 LTS Hardy"
date: 2009-04-24
forum: General Help
---

### Post by 0akash0 on 2009-04-24
**Shutdown Err : Ubuntu 8.04 LTS**

  sysifo://
_____________________________________________________________________________________________

I am using Release Ubuntu 8.04 LTS (hardy) with Kernel Linux 2.6.24-19-generic on GNOME 2.22.2. RAM - 2 gigs, Processor AMD 64x2 dual core 4000+ with nVidia(M2N-XE) motherboard. Router - MTNL UT-300R2U.
_____________________________________________________________________________________________

problem://
_____________________________________________________________________________________________

Whenever I shutdown my desktop, I get the following message if the router in turned on and some different message when the router is turned off, I never get a clean system shutdown.
_____________________________________________________________________________________________

Router still on:
___________________________________________________________________________________________

NetworkManager : <info> Caught termination signal

NetworkManager : <debug> [1240508519.721002] nm_print_open_socks() : Open Sockets List:

NetworkManager : <debug> [1240508519.721002] nm_print_open_socks() : Open Sockets List Done.

NetworkManager : <info> Deactivating device eth0

NetworkManager : <WARN> nm_hal_deinit() : libhal shutdown failed - Connextion is closed.

NetworkManager : nm_dbus_singal_device_status_change : asserion ' cb_data -> data -> dbus_connection ' failed
NetworkManager : nm_dbus_singal_device_status_change : asserion ' cb_data -> data -> dbus_connection ' failed
NetworkManager : nm_dbus_singal_device_status_change : asserion ' cb_data -> data -> dbus_connection ' failed
___________________________________________________________________________________________

How do I fix this??? :confused::confused::confused:

---

### Post by Yashiro on 2009-04-24
Your shutdown will be fine. It's a bug in Network Manager.

If it really annoys you then remove Network Manager and control your net connection using the /etc/network/interfaces file instead.

---


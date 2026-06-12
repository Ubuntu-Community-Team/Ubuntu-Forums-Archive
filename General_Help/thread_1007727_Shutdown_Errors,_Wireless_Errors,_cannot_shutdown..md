---
title: "Shutdown Errors, Wireless Errors, cannot shutdown."
date: 2008-12-10
forum: General Help
---

### Post by Soupcan on 2008-12-10
When I attempt to Shutdown or Restart (I don't know about Suspend/Hibernate) I see the following error, and the computer hangs. The only way to turn my computer off is to hold the power button. About 2-3 minutes after I log in, my connection becomes extremely slow. I get ~12kbps when I should be getting around 7000kbps, and this only started happening recently. 
```
NetworkManager:  <WARN> nm_signal_handler(): Caught signal 15, shutting down normally.
NetworkManager:  <info> Caught termination signal
NetworkManager:  <debug> [1228949902.759516] nm_print_open_socks(): Open Sockets List:
NetworkManager:  <debug> [1228949902.759570] nm_print_open_socks(): 1: wlan0 F:'request_and_convert_scan_results' D:'(null)'
NetworkManager:  <debug> [1228949902.759620] nm_print_open_socks(): Open Socket List Done
NetworkManager:  <info> Deactivating device eth0
NetworkManager:  <info> Deactivating device wlan0
NetworkManager:  <info> Activation (wlan0): cancelling...
NetworkManager:  <info> Activation (wlan0): cancellation handler scheduled...
NetworkManager:  <info> Activation (wlan0): waiting for device to cancel activation.
NetworkManager:  <info> Activation (wlan0): cancellation handled.
NetworkManager:  <info> Activation (wlan0): cancelled.
NetworkManager:  <WARN> nm_hal_deinit(): libhal shutdown failed - Connection is closed.
NetworkManager: nm_dbus_signal_device_status_change: assertion `cb_data->data->dbus_connection' failed
NetworkManager: nm_dbus_signal_device_status_change: assertion `cb_data->data->dbus_connection' failed
NetworkManager: nm_dbus_signal_wireless_network_change: assertion `connection != NULL' failed
```
There may be errors in that block, as I had to write down what I saw by hand.

---

### Post by Soupcan on 2008-12-10
Bump. I'm sorry, but I desperately need help with this.

---

### Post by Soupcan on 2008-12-11
I really need a solution for this. Please help.

---

### Post by Soupcan on 2008-12-13
I posted this two days ago, and no one has even responded. *Please, please help me.*

---

### Post by SPr on 2008-12-13
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/183568/comments/3](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/183568/comments/3)

That is a workaround for this problem on Gutsy but it may work for you unless the shutdown procedure has been drastically altered.

---

### Post by Soupcan on 2008-12-16
> **SPr said:**
> [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/183568/comments/3](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/183568/comments/3)

That is a workaround for this problem on Gutsy but it may work for you unless the shutdown procedure has been drastically altered.
I'm kind of reluctant to try that, but I will. And I'd also like to fix the problems with the wireless speed if possible.

---

### Post by SPr on 2008-12-17
When altering any configs make a backup of the file first, if the changes don't work put the backup back.

```

cp /path/to/config.conf /path/to/config.conf.backup

```
*Edits /path/to/config.conf*
Woops, didn't work.
```

cp /path/to/config.conf.backup /path/to/config.conf

```
There, that's better.

---


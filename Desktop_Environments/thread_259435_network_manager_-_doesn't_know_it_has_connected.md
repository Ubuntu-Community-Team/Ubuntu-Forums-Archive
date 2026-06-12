---
title: "network manager - doesn't know it has connected"
date: 2006-09-17
forum: Desktop Environments
---

### Post by pinegreen on 2006-09-17
I still have problems with network manager. Below is what happens when I plug in the cable (i.e. not a wireless problem and not a hardware problem). 
At the point where I added "**** WORKING" to the log, the eth0 network is up and running, I can connect to various sites, etc. However, network manager still thinks it is down, the dots keep rotating in the applet, and after a while it times out and then it sets eth0 to some stupid default IP at which point it (of course) stops working. 
Any ideas? I am really desperate...


root@proust:/home/anze# NetworkManager --no-daemon
NetworkManager: <information>   starting...
NetworkManager: <WARNING>        main (): nm_data_new: Setting up dbus filter
NetworkManager: <information>   eth0: Device is fully-supported using driver 'e1000'.
NetworkManager: <information>   nm_device_init(): waiting for device's worker thread to start
NetworkManager: <information>   nm_device_init(): device's worker thread started, continuing.
NetworkManager: <information>   Now managing wired Ethernet (802.3) device 'eth0'.
NetworkManager: <information>   ath0: Device is fully-supported using driver 'ath_pci'.
NetworkManager: <information>   nm_device_init(): waiting for device's worker thread to start
NetworkManager: <information>   nm_device_init(): device's worker thread started, continuing.
NetworkManager: <information>   Now managing wireless (802.11) device 'ath0'.
NetworkManager: <information>   Updating allowed wireless network lists.
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <WARNING>        nm_dbus_get_networks_cb (): nm-dbus-nmi.c:522 (nm_dbus_get_networks_cb): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   Will activate wired connection 'eth0' because it now has a link.
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   SWITCH: no current connection, found better connection 'eth0'.
NetworkManager: <information>   Will activate connection 'eth0'.
NetworkManager: <information>   Device eth0 activation scheduled...
NetworkManager: <information>   Activation (eth0) started...
NetworkManager: <information>   Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <information>   Activation (eth0) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <information>   match
NetworkManager: <information>   Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <information>   Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <information>   Activation (eth0) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <information>   Activation (eth0) Stage 2 of 5 (Device Configure) successful.
NetworkManager: <information>   Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
NetworkManager: <information>   Activation (eth0) Stage 2 of 5 (Device Configure) complete.
NetworkManager: <information>   Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   Activation (eth0) Beginning DHCP transaction.
NetworkManager: <information>   Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
NetworkManager: <information>   DHCP daemon state is now 12 (successfully started) for interface eth0
NetworkManager: <information>   Old device 'eth0' activating, won't change.
NetworkManager: <information>   match
NetworkManager: <information>   Old device 'eth0' activating, won't change.

**************WORKING

NetworkManager: <information>   Device 'eth0' DHCP transaction took too long (>45s), stopping it.
NetworkManager: <information>   Activation (eth0) Stage 4 of 5 (IP Configure Timeout) scheduled...
NetworkManager: <information>   DHCP daemon state is now 14 (normal exit) for interface eth0
NetworkManager: <information>   DHCP daemon state is now 14 (normal exit) for interface eth0
NetworkManager: <information>   Activation (eth0) Stage 4 of 5 (IP Configure Timeout) started...
NetworkManager: <information>   No DHCP reply received.  Automatically obtaining IP via Zeroconf.
NetworkManager: <information>   autoip: Sending probe #0 for IP address 169.254.223.103.
NetworkManager: <information>   autoip: Waiting for reply...
NetworkManager: <information>   autoip: Sending probe #1 for IP address 169.254.223.103.
NetworkManager: <information>   autoip: Waiting for reply...
NetworkManager: <information>   Old device 'eth0' activating, won't change.
NetworkManager: <information>   autoip: Sending probe #2 for IP address 169.254.223.103.
NetworkManager: <information>   autoip: Waiting for reply...
NetworkManager: <information>   autoip: Sending announce #0 for IP address 169.254.223.103.
NetworkManager: <information>   autoip: Waiting for reply...
NetworkManager: <information>   autoip: Sending announce #1 for IP address 169.254.223.103.
NetworkManager: <information>   autoip: Waiting for reply...
NetworkManager: <information>   autoip: Sending announce #2 for IP address 169.254.223.103.
NetworkManager: <information>   autoip: Waiting for reply...
NetworkManager: <information>   Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
NetworkManager: <information>   Activation (eth0) Stage 4 of 5 (IP Configure Timeout) complete.
NetworkManager: <information>   Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
NetworkManager: <information>   DHCP returned name servers but system has disabled dynamic modification!
NetworkManager: <information>   Activation (eth0) Finish handler scheduled.
NetworkManager: <information>   Activation (eth0) successful, device activated.
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
************************* NOT WORKING

---

### Post by pod25 on 2006-09-17
I'm no expert and I could be wrong here, but :

Have you tried selecting which card you want to allow access, then set the IP to Static ?

```
sudo nano /etc/network/interfaces
```
Example code below :::::
```
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
```

Worth a try ?

---

### Post by pinegreen on 2006-09-17
No, that is not a problem... I can manually configure eth0 to work with either static or dynamic addresses. So manual configuration works, but if alos just say dhclient eth0, it also works. 
I would like to get automatic networking with network manager and for that purpose you have to comment eth0 out of /etc/network/interfaces, anyway! The problem is that network manager doesn't get it that dhcp got the address (it also happens with wireless)

---

### Post by pinegreen on 2006-09-19
Finally resolved it:
on deinstallation there were some rogue whereami exit-hook scripts that broke the dhclient exit... Now it works like a charm!

---

### Post by xnij on 2006-12-14
I've got the same problem.... I'm guessing that avahi-autoipd is messing with dhcp client?

To get things working again I have to kill NetworkManager and run dhclient on my (wired) interface.

Any ideas?

---

### Post by mcduck on 2006-12-14
Network Manager only works for me if I have all my network interfaces unconfigured in Gnome's Network Settings.. You could try that.

---

### Post by xnij on 2006-12-15
> **mcduck said:**
> Network Manager only works for me if I have all my network interfaces unconfigured in Gnome's Network Settings.. You could try that.

I had a look at the Gnome Net Settings and nothing is active there... Thanks for the suggestion.


pinegreen: What did you do to clear out the "exit-hooks" scripts? There's a file /etc/dhclient-exit-hooks with one line: "sh /etc/init.d/firestarter start". Was it that file you removed?

I'll give it a go. Getting a bit desperate here. :neutral:

---

### Post by xnij on 2006-12-18
No, nothing active in Gnome's Network Settings. 

I uninstalled firestarter which removed the exit-hooks file and I thought I had it working, but, alas, it still doesn't work; still looping around the DHCP client configuration. :(

---

### Post by xnij on 2006-12-19
Ok, found what the problem was. I was getting this in my syslog:
[...]
Dec 19 15:07:57 localhost NetworkManager: <information>^IDeactivating device eth3. 
Dec 19 15:07:58 localhost avahi-autoipd(eth2)[8222]: Successfully claimed IP address 169.254.9.98
Dec 19 15:07:58 localhost avahi-autoipd(eth2)[8222]: fopen() failed: Permission denied
Dec 19 15:08:03 localhost NetworkManager: <information>^Istarting... 
[..]

It seems there's a problem in /etc/dhcp3/dhclient-exit-hooks.d/zzz_avahi-autoipd (or avahi-autoipd itself) which caused the loop. I've now moved the 2 avahi files from the enter and exit hooks directories and now it finally works.

Not optimal, but at least it works now.

---


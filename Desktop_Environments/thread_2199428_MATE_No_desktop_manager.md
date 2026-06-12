---
title: "MATE No desktop manager"
date: 2014-01-13
forum: Desktop Environments
---

### Post by Sega dude on 2014-01-13
I recently installed MATE and I love it but it seems my network manger is missing. If I right click and add to panel, there is no network manager option. How can I get it back?

---

### Post by oldrocker99 on 2014-01-13
I use MATE and have a network indicator on installation. I don't know what your problem is if you were able to get online.

---

### Post by tgalati4 on 2014-01-13
There is no network manager to add to the panel.  There is *nm-tool* to see if your network is working:

Open a terminal:

```
nm-tool
```

Then there is *nm-applet*, which plants itself in the system tray, but not the panel.

Maybe it is not running?

tgalati4@Mint14-Extensa ~ $ ps -ef | grep nm
nobody     988   799  0 Jan06 ?        00:00:01 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/var/run/sendsigs.omit.d/network-manager.dnsmasq.pid --listen-address=127.0.1.1 --conf-file=/var/run/nm-dns-dnsmasq.conf --cache-size=0 --proxy-dnssec --enable-dbus=org.freedesktop.NetworkManager.dnsmasq --conf-dir=/etc/NetworkManager/dnsmasq.d
root      1197     1  0 Jan06 ?        00:00:01 nmbd -D
tgalati4  2046  1830  0 Jan06 ?        00:00:32 **nm-applet**
root     24791   799  0 19:16 ?        00:00:00 /sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/sendsigs.omit.d/network-manager.dhclient-wlan0.pid -lf /var/lib/dhcp/dhclient-a84bee18-22b3-4287-a4ba-7ffc6cf55acb-wlan0.lease -cf /var/run/nm-dhclient-wlan0.conf wlan0
tgalati4 25027  2483  0 19:37 pts/0    00:00:00 grep --colour=auto nm

---


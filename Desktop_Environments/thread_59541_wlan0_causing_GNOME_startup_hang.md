---
title: "wlan0 causing GNOME startup hang"
date: 2005-08-24
forum: Desktop Environments
---

### Post by tehwa on 2005-08-24
Hi,

I have used ndiswrapper to get my wireless up. It works well, however whenever I log out/reboot, GNOME hangs on a new session startup.

basically, I have modified /etc/network/interfaces to be:

```

# Used by ifup and ifdown. See the interfaces(5) manpage or
# /usr/share/doc/ifupdown/examples for more information.

iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
name WG311T
wireless_essid   NETWORK
wireless_channel 6
wireless_mode    managed

```

If I boot up GNOME without the wlan0 entry, just the loopback entry, GNOME will boot happily.

If I boot with the wlan0 included in the file, GNOME hangs before displaying the ubuntu image/gnome application startup icons. In which case I am required to restart X, log into terminal, edit /etc/network/interfaces to remove the wlan0 entry and then restart my machine.

I suspect restarting my machine could be replaced with a command or two, but I don't know them.

If anyone can help me out with how to remedy this (is my /interfaces file bad?)  please do.

---

### Post by tehwa on 2005-08-26
Problem resolved after a system wide reinstall, following a monumental cockup involving libwx* and playing as root...

---


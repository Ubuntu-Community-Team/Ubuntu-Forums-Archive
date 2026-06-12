---
title: "networkmanager wep startup"
date: 2005-10-17
forum: Desktop Environments
---

### Post by t.knopp on 2005-10-17
Hi!

I have upgraded my ubuntu to breezy and installed networkmanager, which is really cool. My only Problem is, when I turn on WEP ubuntu hangs at startup, when it tries to access the network. I think that the networking init script is independent from networkmanager and doesn't know the WEP-key which is in the gnome-keyring-manager. Do I have to disable that init script, or how is it supposed to work?

Tobi

---

### Post by odin on 2005-10-17
I'm not in breezy yet but have you tried to configure this in /etc/network/interfaces?

You should have something like this:

auto eth0 (my wifi device is eth0 yours could be another one)
iface eth0 inet dhcp (if you get your ip via dhcp)
wireless-essid "your network essid"
wireless-key "your wep key"

As far as I know the init script for networking takes parameters from this file so it should configure your network interfaces right if you put them here.

Well,hope this helps a bit

---

### Post by t.knopp on 2005-10-17
the problem is that I have multiple WEPs, depending where I use the laptop. thats why I want too use networkmanager.

---


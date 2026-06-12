---
title: "Dhclient?"
date: 2005-12-27
forum: General Help
---

### Post by rensu on 2005-12-27
Yesterday was my electric interrupted. After that my server went up automatecally but it didn't start Internet. For that i had to put it manually with dhclient. Question: How i can set it so that it goes automatecally after every crash?

---

### Post by rensu on 2005-12-28
Nobody who can help me ?:( Its prettu boring to type always at startup dhclient on server to get inet.

---

### Post by ape on 2005-12-28
rensu,

  What does your /etc/network/interfaces file look like?

  Does the output from the `dmesg` command show anything failing in the network area on boot up?

---

### Post by rensu on 2005-12-28
Should it look like this?:
iface eth0 inet dhcp

To get the dhcp automatecally after every reboot?

---

### Post by 0MG on 2005-12-28
that should do it. 

Another way to do it (through the gui) is to double-click the network connection icon in your panel (looks like two little PC monitors), select eth0, configure, go into the properties for eth0, set it up as enabled with dhcp.

---

### Post by rensu on 2005-12-28
Sry i cant do that because im running only console:(

---

### Post by ape on 2005-12-29
You need to also make sure that you have something like

   auto lo eth0

in your /etc/network/interfaces file.

And, again, anything in your dmesg output that would show an attempt to run dhclient prior to your ethernet adapter being initialized?

---


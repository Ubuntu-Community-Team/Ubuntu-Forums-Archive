---
title: "Any particular reason why NetworkManager doesn't work?"
date: 2007-01-23
forum: Desktop Environments
---

### Post by Quillz on 2007-01-23
So I've installed the NetworkManager applet to make it easier when dealing with multiple wireless networks. I reboot and it appears, and it says that I'm not connected to any wireless networks. But oddly enough, I am. I'm typing this very message on a wireless network. When I click on the icon, I find that a wireless option isn't even available. All I see is a grayed out "wired." Does anyone know why the app doesn't recognize that I'm connected right now, and is there a way to fix it?

---

### Post by ComplexNumber on 2007-01-23
> **Quillz said:**
> So I've installed the NetworkManager applet to make it easier when dealing with multiple wireless networks. I reboot and it appears, and it says that I'm not connected to any wireless networks. But oddly enough, I am. I'm typing this very message on a wireless network. When I click on the icon, I find that a wireless option isn't even available. All I see is a grayed out "wired." Does anyone know why the app doesn't recognize that I'm connected right now, and is there a way to fix it?
install an application called BUM(Boot Up Manager). i find it an extremely useful applications.
i suspect that it may well be that the network manager applet daemon isn't running. BUM will allow you to change that, and it it will allow you to start up the daemon at boot-up.

---

### Post by Quillz on 2007-01-24
> **ComplexNumber said:**
> install an application called BUM(Boot Up Manager). i find it an extremely useful applications.
i suspect that it may well be that the network manager applet daemon isn't running. BUM will allow you to change that, and it it will allow you to start up the daemon at boot-up.
Okay, I've installed BUM, but I'm not exactly sure what daemon I'm supposed to enable.

---

### Post by andyeddy525 on 2007-01-24
buuuuuump

---

### Post by tombott on 2007-01-24
From your screenshot I see that the Ubuntu standard network monitor icon is showing.

Did you edit your /etc/network/interfaces ?

```

sudo gedit /etc/network/interfaces
```

You should put # in front of all network connections you wish NetworkManager to manage apart from auto lo

So for example -

```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp
#wireless-essid myrouterhere
#wireless-key s:passphrasehere

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp


iface eth0 inet dhcp

auto eth0
```

As you can see I have left my ethernet NIC be managed by Ubuntu where as everything else gets managed by NetworkManager

Hope that helps.

---

### Post by ComplexNumber on 2007-01-24
> **Quillz said:**
> Okay, I've installed BUM, but I'm not exactly sure what daemon I'm supposed to enable.
the network manager daemon/service.

---

### Post by orb9220 on 2007-01-24
Tombott is right this is a  common fix for network-manger I have to do it everytime I do a clean install.

sudo gedit /etc/network/interfaces
and comment out # the lines shown in his.

---


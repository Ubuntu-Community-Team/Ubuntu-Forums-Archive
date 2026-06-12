---
title: "home folder on network share - wireless networking"
date: 2009-03-12
forum: General Help
---

### Post by moroff on 2009-03-12
posts mention problem mounting share during boot as wireless connection not up yet and boot will hang/delay.  how to?

---

### Post by heindsight on 2009-03-12
Try phrasing your questions in full sentences.

You need your wireless connection brought up at boot, rather than after you log in. This means you can't use the network-manager applet, you have to configure your network in /etc/network/interfaces and perhaps also in /etc/wpa_supplicant/wpa_supplicant.conf instead.

Have a look at the manuals:
```
man interfaces
```
and
```
man wpa_supplicant.conf
```

As an example, my wireless network at home uses WPA encryption with a pre-shared-key. I use a configuration like:

```
#/etc/network/interfaces
# This file should be owned by root:root and readable by everyone

# bring up lo and eth1 automatically at boot
auto lo eth1

#configuration for lo
iface lo inet loopback

# configuration for eth1
iface eth1 inet dhcp
    wpa_conf /etc/wpa_supplicant/wpa_supplicant.conf

```

```
# /etc/wpa_supplicant/wpa_supplicant.conf
# This file should be owned by root:root and NOT world readable

# allow configuration file to be updated by tools such as wpa_cli
update_config=1

# Control interface for wpa tools
ctrl_interface=/var/run/wpa_supplicant

# Network description
network={
    id_str="MyNetwork"
    ssid="MyNetworkSSID"  
    key_mgmt=WPA-PSK
    proto=WPA
    group=TKIP
    pairwise=TKIP
    psk="MyNetworkKey"
}

```

There are several ways to configure it, you don't really need the wpa_supplicant.conf file (you can put all the network specific options there straight into the /etc/network/interfaces file, but I prefer to keep them separate.

---

### Post by moroff on 2009-03-12
thank you.

i did also read mention of mounting share after boot at login time...

could that be simpler or better for this linux newbie?

could i mount it in a login script...

---

### Post by heindsight on 2009-03-12
The problem is that your home directory has to be mounted when you log in. However, if you use the network manager applet to manage your network connection, then the network only becomes available AFTER you log in. 
Clearly this can't work if your home directory is mounted over the network.

This means you have to bring up the network before you can log in (and then you may as well mount your home directory as soon as the network is available).

---

### Post by heindsight on 2009-03-13
I'm afraid setting something like this up will require you to learn a bit about network configuration, but with some help from these forums it shouldn't be too hard.

First off, we'll need a bit more information about your current set up and exactly what you're trying to achieve.

Are you currently able to log in using a local home directory (instead of one mounted over the network)?

Do you have your wireless network working at all? If so, how did you configure it?

Where are you hoping to mount your home directory from?

---


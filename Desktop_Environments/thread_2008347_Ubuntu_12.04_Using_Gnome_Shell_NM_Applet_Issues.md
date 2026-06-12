---
title: "Ubuntu 12.04 Using Gnome Shell NM Applet Issues"
date: 2012-06-22
forum: Desktop Environments
---

### Post by metallica1973 on 2012-06-22
I installed the latest GNOME SHELL and noticed that dhclient assigns an address to eth0 fine but when I go into the GUI and look at network connection in the upper right hand corner, it does not show any profile of what I already have and when I attempt to add a profile everything is grayed out. It appears to be something with permission. Any ideas?

---

### Post by metallica1973 on 2012-06-23
I think it may be a bug:

This is the scenario:

I installed a barebones  Ubuntu 12.04 using GNOME-SHELL on a usbstick(work related project). All worked fine from the laptop that I did the installation from. It grabbed an ip address automatically assigning the nic (eth0) and the wireless interface (wlan0) correctly. The nm-applet worked fine when you clicked the upper right hand corner in which you could edit the profile(eth0) and or (wlan0) respectively. 

So in testing I decided to test this usbstick on several other laptops and desktop to see how things went(Thinkpads,EliteBooks and etc). All worked fine except that Ubuntu is randomly reassigning the interfaces eth1,eth2,wlan1,wlan2 and not consitently keeping them eth0, eth1 like our previous build using Ubuntu 10.04.  I can see what is happeneing. When I look at the /etc/NetworkManager/NetworkManager.conf:

```

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

```

Network Manager is not managing what is in /etc/network/interefaces:

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

because the nic interfaces are changing random to something else eth1,eth2,wlan1,wlan2 on the other machines that I am using for testing thus disabling the nm-applet icon from appearing in right hand corner on the panel. Ubuntu is randomly assigning them which can be seen under /etc/udev/rules.d/70-persistent-net.rules:

```

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.3/0000:44:00.0 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:27:10:bd:8a:88", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="88:ae:1d:b6:a3:f7", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (r8169)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1e:33:3d:e0:d7", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (iwl4965)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1f:3b:80:8b:21", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.5/0000:07:00.0 (tg3)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="88:ae:1d:2e:a9:14", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0/ssb0:0 (b43-pci-bridge)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="78:e4:00:84:b9:68", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0 (e1000)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:25:32:59:64", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1e.0/0000:02:02.0 (ath5k)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0e:9b:6e:27:b1", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan3"

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0 (e1000)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:25:32:59:64", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1e.0/0000:02:02.0 (ath5k)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0e:9b:6e:27:b1", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0 (e1000)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:25:32:59:64", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1e.0/0000:02:02.0 (ath5k)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0e:9b:6e:27:b1", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1e.0/0000:02:02.0 (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0e:9b:6e:27:b1", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.5/0000:07:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="88:ae:1d:2e:a9:14", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0/ssb0:0 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="78:e4:00:84:b9:68", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"

```

In addition to that randomly reassignment of the nic interfacing, ip address are not being assigned to the nics because they do not reside in /etc/network/interaces as seen in the above.

---

### Post by metallica1973 on 2012-06-25
This appears to have worked:


[http://askubuntu.com/questions/154389/how-does-dhclient-get-called-under-12-04]("http://askubuntu.com/questions/154389/how-does-dhclient-get-called-under-12-04")

---


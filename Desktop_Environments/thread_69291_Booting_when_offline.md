---
title: "Booting when offline"
date: 2005-09-26
forum: Desktop Environments
---

### Post by matva on 2005-09-26
When i start up, kubuntu seems to test for a net connection (like during boot process). A lot of the time i am offline, and it takes like 2 minutes for that phase to be "OK"ed. How do i skip, or disable it? 

Also, how to i easily manage my network connections. I switch between a wireless and wired connection a lot, and i have yet to find a way to easily switch between the two. Right now i am having to go to control panel and disable one and enable the other which takes awhile.

---

### Post by KPingus on 2005-09-26
Look into the file /etc/network/interfaces. Your ethernet connection probably has the name eth0. The reason why it tries to initiate a connection at boot time is probably because is your /etc/network/interfaces you have a line that says "auto eth0". Remove or comment out that line. You'll want to have something that looks like:

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
iface eth0 inet dhcp

```

Later, if you want the ethernet connection to be initiated as soon as, or whenever, your ethernet cable is plugged in, you can add something such as

```

mapping hotplug
        script grep
        map eth0

```

To easily switch between different connections, look into 'netapplet' by Robert Love. It was designed for Gnome but I use it under KDE. Other options, for wireless connections include pywireless and wireless-assistant (see [www.kde-apps.org)](www.kde-apps.org)).

---

### Post by matva on 2005-09-26
So when i comment that line out, will a connection be attempted to be made when i actually login? I mean, i dont want to have to do anything when i login to get the net working, i just dont want it to connect while im booting. 

ill check at the programs you mentioned.

---


---
title: "wireless card for thinkpad t41 not working"
date: 2006-01-26
forum: Desktop Environments
---

### Post by shabzone on 2006-01-26
I recently installed breezy badger and the first thing I noticed was that my wireless is not working. I am using a thinkpad t41 with an Intel PRO/Wireless LAN 2100 3B Mini PCI. When I go to device manager, I see AR5212 802.11abg NIC--which I assume is the wireless card. However, I do not see any ath0 options in network settings. The only thing there is ethernet connection (eth0). I remember my wireless used to work striaght out of the box with hoary, so please help!:confused: 

Thanks in advance.

---

### Post by Lambert on 2006-01-26
If it's an atheros chipset, make sure you have linux-restricted-modules-(kernel)
installed as the madwifi driver is part of that package. replace kernel with the kernel version you're running.

---

### Post by shabzone on 2006-01-26
Hmm, I have kernel 2.6.12-10-386 and linux-restricted-modules is installed (version 2.6.12.4-11.1) but the wireless still does not show up in network connections.

---

### Post by SickTwist on 2006-01-28
I just bought a T41 (got it delivered yesterday :) ) and it has the same wireless chipset that your laptop does.  Our laptops use the Atheros chipset which is supported by the [madwifi]("http://madwifi.org/") project. Madwifi is part of the restricted modules package as Lambert mentioned.

You may need to add a line to /etc/network/interfaces that looks like this:
**iface ath0 inet dhcp**

To do that, type **sudo gedit /etc/network/interfaces** at a terminal and type the line. Also, make sure there are no lines that look like "auto eth0" or "auto ath0". However, there must be a line that says "auto lo" so leave that one alone.

I recommend that you install the network-manager package as it seems to work great for me so far. To make it launch when you log in, go to System-->Preferences-->Sessions, click on the "Startup Programs" tab, click "Add" and type "nm-applet" (without quotes) for the command. You can change the startup number to something lower than 50 to make it start sooner. It will start automatically the next time that you log in. Once it launches, you'll see an icon in the system tray area on the panel. If your laptop is connected to a wired connection, it will use that automatically. If there is no wired connection, network-manager will list the access points in the area and let you pick one.

Good luck and let us know if you need more help.

---

### Post by doepain on 2007-05-07
I just installed Ubuntu Feisty Fawn on my ThinkPad t41.  I notice the Wifi indicator flashingsteadily, but I am not connected to anything.

Perhaps it is because the WAP has wep enabled where I am.
I tried following the Wifi TS guide but found parts of it hard to follow and unclear.

Does anyone know to configure a WAP profile with wep enabled.
Also downloaded NetworkManager, but have not yet found any detailed articles on how to install and configure it.

All help greatly appreciated.

---

### Post by mollywolly on 2007-06-10
Alas, I have the same problem.  Tried three or four of the recommendations, but nothing works.  My card sees the wireless networks but does not connect; to either a WEP or WPA PSK type. I tried wpasupplicant mod's, and next I'll try the ndiswrapper -when I can get my hands on an xp install program.  Hate to have to fall back to windows for anything, but....  My wireless card is a Cisco 80211b.  If it works, I'll let you know.

---

### Post by doepain on 2007-06-11
I did eventually get the wireless to work.  Iwas actually working the entire time I just was unaware of of it be cause the the location I was working from required a WEP... and I was to lazy to ask my colleagues what it was.

You have to use the network manager/monitor right-click on it from th e notifications area and specify which availible SSID to connect too, and then click configure and add the encryption method.

It stinks in one way because I have not yet figured out away to save multiple Wifi profiles, so I have to carry a list of encryption keys to plug-in.

If these instructions are a little vague or to genralized I appologize I am not working from my Ubunto system so I am trying to recall the steps I took to get on the wifi.

---


---
title: "Wireless network"
date: 2006-01-01
forum: General Help
---

### Post by Brian Sisco on 2006-01-01
I have laptop set up to dual-boot Windows XP and Ubuntu 5.10 and when it is running Windows I can use the internet just fine (that how I'm posting this :) ). 

How do I configure Ubuntu to use my house's wireless network? The other computers on the network all run Windows.

---

### Post by Jammy_Stuff on 2006-01-01
You need to find out what wireless card you are using and then someone will be able to tell you if it will work. You'll need to set it up using ndiswrapper.

---

### Post by Lambert on 2006-01-01
More information is needed but you can go through these links to see if you can get wireless going.

[https://wiki.ubuntu.com/WiFiHowto](https://wiki.ubuntu.com/WiFiHowto)
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

---

### Post by Brian Sisco on 2006-01-01
What information is needed? My wireless card is a Broadcom 802.11b/g WLAN. My computer is an HP Pavilion ZD7000.

---

### Post by Jammy_Stuff on 2006-01-01
Do you have an exact model number?

---

### Post by Brian Sisco on 2006-01-01
Sorry, I edited in the model number before seeing your new post.

---

### Post by Jammy_Stuff on 2006-01-01
I meant the exact model number of the Broadcom card.

---

### Post by Brian Sisco on 2006-01-02
The model number of the card is Broadcom BCM94306MPSG.

---

### Post by psylvester on 2006-01-04
sylvester@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

sylvester@ubuntu:~$


This is whatI get, I dont get wireless when i login Via Linux, It works fine with Xp.
I have two OS on my laptop.
Can anyone help me to fix this problem.


sylvester@ubuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp


Thanks
Sylvester.

---


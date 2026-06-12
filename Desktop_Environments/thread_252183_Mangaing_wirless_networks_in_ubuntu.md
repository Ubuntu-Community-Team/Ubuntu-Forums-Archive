---
title: "Mangaing wirless networks in ubuntu"
date: 2006-09-06
forum: Desktop Environments
---

### Post by nkj on 2006-09-06
here is the situation , I want my laptop to automatically connect to the school wireless network when i m on campus and when i m at home it should connect both to my hardwire connection and wifi , 
how to do this so that it switches automatically between the two networks.

---

### Post by jimbob on 2006-09-06
apt-get install network-manager

---

### Post by killkoy on 2006-09-06
you can use network manager.
```
sudo aptitude install network-manager-gnome
```
then type
```
sudo cp /etc/network/interfaces /etc/network/interfaces.backup
sudo gedit /etc/network/interfaces
```
and delete all lines aso that it looks like this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
```
Then restart your computer and connect to the network using the taskbar applet thing when logged on.
If network manager cant connect type
```
sudo mv /etc/network/interfaces.backup /etc/network/interfaces
sudo ifup -a
```to use your original settings

---

### Post by dannyboy79 on 2006-09-06
i would strongly suggest wifi-radar. it doesn't AUTOMATICALLY connect when you are in range of the access point but it does have a gui for you to go to and view all available wireless networks and whether or not they are secure (wep or wap) and then you can click on it, then click connect and you're good to go!!!!

---

### Post by Crayoneater on 2006-09-06
you could try gtk-wifi for wireless connection....

---

### Post by Atomic Dog on 2006-09-06
> **dannyboy79 said:**
> i would strongly suggest wifi-radar. it doesn't AUTOMATICALLY connect when you are in range of the access point but it does have a gui for you to go to and view all available wireless networks and whether or not they are secure (wep or wap) and then you can click on it, then click connect and you're good to go!!!!


Wifi-radar is the bomb.  Mine does seem to connect to preferred networks when in range...at least between work and home.

---


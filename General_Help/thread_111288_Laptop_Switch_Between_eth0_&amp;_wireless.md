---
title: "Laptop Switch Between eth0 &amp; wireless"
date: 2006-01-02
forum: General Help
---

### Post by goneskiing on 2006-01-02
Have a Dell Inspiron laptop - eth0 works fine and it is setup as DHCP for the office - when I'm travelling I would like to use wireless instead - I have a built-in wireless and installed NDIS wrapper and have a driver module installed.  What do I need to set up to switch to wireless on the road?  What settings are required for "normal" hot spots?  Is there an easy way to switch between eth0 and wireless ?  thanks.

---

### Post by Jammy_Stuff on 2006-01-02
Just go to System > Administration > Network ,disable eth0 and enable wlan0 when you need to change.

---

### Post by goneskiing on 2006-01-02
okay, thanks.  I am pretty helpless on this so need a step by step process:
1) my wireless card is now activated via a modprobe - should that stay that way or be added somehow to /etc/init.d/??  (see my steps below)
2) Do I need any special WEP or ESID codes for a "regular" hot spot (which I assume doesn't have WEP) but I'm not sure how this all works.  
3) is there any gnome applet for managing wireless ? 

my current instructions to activate card:
sudo modprobe ndiswrapper
sudo dmesg
sudo iwlist wlan0 scan
sudo iwconfig wlan0 essid ???
iwconfig wlan0 enc <wep key ??>
sudo dhclient wlan0
sudo ping -c 3 [www.ubuntu-linux.nl](www.ubuntu-linux.nl)

---


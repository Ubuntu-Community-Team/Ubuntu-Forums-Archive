---
title: "error msg on bootup (NetworkManager)"
date: 2006-06-15
forum: Desktop Environments
---

### Post by hoistyler on 2006-06-15
Hi all
I am getting an error msg box on every bootup saying
"The NetworkManager applet could not find some required resources. It cannot continue"
after installing some app using automatix. 
I can't find what is affected everything seems to work fine.

What does that msg mean and how can i get rid of it?

---

### Post by Andykvakk on 2006-06-15
Try to run ```
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/
```. This helped me :-)

---

### Post by hoistyler on 2006-06-15
This helped me too i'm not getting the error msg
Thanks 

now there is a networks icon in the task tray, but the problem is that it's just sitting there doing nothing. It says "no network connection" where i'm connected to internet thru network

---

### Post by Andykvakk on 2006-06-15
You have to disable Ubuntus internal network manager. To do this write sudo gedit /etc/network/interfaces in a terminal. The put an # in front of all the lines exept "auto lo". There is a more graphical way, go to System - Network and open every connection and remove "this is configured" on every card. (I use norwegian ubuntu, so i'm not sure what it says on english.). Reboot computer and you will be able to use network manager.

---

### Post by hoistyler on 2006-06-15
I followed the gedit way but boot up time has greatly increased(i can have a cup of coffee during bootup), and also internet is not working but the icon on the top says the network is connected. It's like the other way around

---

### Post by Andykvakk on 2006-06-15
This is how my interfaces file look like ```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

```.

After bootup, see if you kan select a wireless network by left clicking on the network icon next to the clock.

---

### Post by hoistyler on 2006-06-15
It now works!

Thanks for your help

---


---
title: "Network-Admin not working properly"
date: 2006-03-19
forum: Desktop Environments
---

### Post by danrom on 2006-03-19
I have installed ndiswrapper and running perfectly with no problems. Card is detected and everything on first try. The problem I am having now Network-Admin, I set the default gateway device to wlan0 my wireless card interface name. As I hit ok I notice it does not save wlan0 as the default gateway. All settings were saved accept the default device, could some one assist me and tell me where the Network-Admin configuration file is located.

---

### Post by Zelut on 2006-03-19
Two things come to mind..
You could deactivate the other devices.  I would think, at that point, it would have to stay as wlan0.

Otherwise the networking interface file is found in /etc/networking/interfaces.  Mine looks similar to this (I have eth0 & wlan0).  Below are the last lines in my file.

iface wlan0 inet dhcp
wireless-essid <my wireless name>
auto wlan0

iface eth0 inet dhcp
auto eth0

---

### Post by danrom on 2006-03-19
All other devices were disabled from the start, sorry for not mentioning this. I copied the wireless settings on my laptop exactly to my desktop and still not having positive results. I noticed DHCP does is not working and I see the LED on my card flickering indicating that it is communiticating with the modem. When the machine is not 'connected' or the card has yet to be told what to connect to the LED is solid. Thanks for replying :)

---

### Post by danrom on 2006-03-20
Can some else please try to help me?

---

### Post by danrom on 2006-03-21
Sorry for double posting but I would really like to use this os on my desktop. As well for network-admin is crashing when I set wlan0 as default gateway device.

---

### Post by Zelut on 2006-03-21
Well you could try the command-line setup.  There is a file where you can specify which devices, dhcp/static, etc.  You might have luck trying that but it sounds like it might be a hardware issue if its locking the entire machine.

take a look at /etc/networking/interfaces file (sudo gedit /etc/networking/interfaces).  Below is the output of my file including eth0 & wlan0.

(last lines in the file)
iface wlan0 inet dhcp
wireless-essid <your-broadcast-name>
auto wlan0

iface eth0 inet dhcp
auto eth0

---

### Post by danrom on 2006-03-21
Thanks for the fast reply :).

I have already done and this and have redid this to make sure, but the default gateway device still will not stay wlan0. The connection can be made and is active but does not mean anything if the default device is not the device that is connected.

---

### Post by danrom on 2006-03-21
Turns out anything that I set as my default gateway crashes network-admin. I cant even ftp to my xbox via cat10 on eth0.

---


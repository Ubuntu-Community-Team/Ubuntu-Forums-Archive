---
title: "IP configure help"
date: 2008-12-13
forum: General Help
---

### Post by Linux408 on 2008-12-13
hello i wish to setup ubuntu much like i did my ps3 its connects to the router as 192.168.1.100 , i want ubuntu to join the router as 192.168.1.99 for example so i can make setting in the router and not worry about the router assigning another pc that address, how to i go about doing this ?

thanks guys / gals

---

### Post by tigerstripedcat on 2008-12-13
There are two ways:

1) You have the router detect the MAC address of your computers and assign them specific addresses, but your computers will all use DHCP and request what the server sends

2)  You don't configure the router to do this MAC detection, but rather have the particular computers set up for a "STATIC IP".  If you want to do this you'll need to configure this in your /etc/network/interfaces, this will force the ip to be static rather than using DHCP which varies depending on what is active on the network at the time.  For example, mine says:

# The primary network interface
iface eth0 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1


if it said:
iface eth0 inet dhcp 

Then it would request, rather than tell, the router what it wanted.

TSC

---

### Post by Linux408 on 2008-12-13
> **tigerstripedcat said:**
> There are two ways:

1) You have the router detect the MAC address of your computers and assign them specific addresses, but your computers will all use DHCP and request what the server sends

2)  You don't configure the router to do this MAC detection, but rather have the particular computers set up for a "STATIC IP".  If you want to do this you'll need to configure this in your /etc/network/interfaces, this will force the ip to be static rather than using DHCP which varies depending on what is active on the network at the time.  For example, mine says:

# The primary network interface
iface eth0 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1


if it said:
iface eth0 inet dhcp 

Then it would request, rather than tell, the router what it wanted.

TSC
cool after i get done with this torrent ill try that, So I juat have to edit that file and paste what you posted right sounds easy enough

---

### Post by Linux408 on 2008-12-13
> **tigerstripedcat said:**
> There are two ways:

1) You have the router detect the MAC address of your computers and assign them specific addresses, but your computers will all use DHCP and request what the server sends

2)  You don't configure the router to do this MAC detection, but rather have the particular computers set up for a "STATIC IP".  If you want to do this you'll need to configure this in your /etc/network/interfaces, this will force the ip to be static rather than using DHCP which varies depending on what is active on the network at the time.  For example, mine says:

# The primary network interface
iface eth0 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1


if it said:
iface eth0 inet dhcp 

Then it would request, rather than tell, the router what it wanted.

TSC
ok i pasted what you posted into that file and reconnected checked the ip and it was still 192.168.1.3 when i set it to be 192.168.1.98 also i think what you posted is for Ethernet im wireless if that helps any ?..

---

### Post by tigerstripedcat on 2008-12-22
First make sure you don't have duplicate entries.  If you're using wireless, you might have better luck using the gui and having it do it.  Run your networkmanager (I'm not sure what it is in ubuntu) and you should have a setting in there to set up a static ip for a particular AP.  If you want to do it through that file you need to use 

iface ra0 inet static

OR 

iface wlan0 inet static

OR 

iface wifi0 inet static

depending on the name of your wifi interface.  You can type ifconfig to check.  I would try and set this up with the GUI though, it would probably work better.

TSC

---


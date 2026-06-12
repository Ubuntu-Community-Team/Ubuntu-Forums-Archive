---
title: "help"
date: 2006-04-22
forum: Desktop Environments
---

### Post by adnaann on 2006-04-22
I GOT IBM T42 AND I INSTALLED UBUNTU ON IT MY LAN CARD IS WORKING OUT OF BOX BUT I GOT SERIOUS PROBLEMS WITH MY WIRELESS CARD
I INSTALLED network-manager THE PROBLEM IS THAT IT DONT SHOWS THE
64BIT ENCRYPTION IN THE TABS , AND AS 64BIT ENCRYPTED KEY IS USED ON MY OFFICE NETWORK AND I GOOOGLED ALOT BUT CANT FIND ANY THING ABOUT HOW TO CHANGE YOUR ENCRYPTION FROM 128 BIT TO 64BIT AS I GUESS THATS THE ONLY THING KEEPIN ME DISSCONNECTED

ANYBODY KNOWS HOW TO DO IT ??

---

### Post by sto6ma9ch on 2006-04-22
I've never had issues with entering a WEP key in GNOME's network setings utility, but here's how to set a WEP key from the command line anyway:

Type the following to open your network interface configuration file in a text editor.
```
sudo gedit /etc/network/interfaces
```

Look for the section that defines your wireless device (wifi0, eth0, ath0, etc.). Using a static IP address, it will look something like this.
```
iface ath0 inet static
address 192.168.XXX.XXX
netmask 255.255.255.0
gateway 192.168.XXX.XXX
wireless-essid some_access_point
wireless-key XXXXXXXXXXXXXXXX
```

You can use the "wireless-key" option to specify the WEP key. If you know the Hexadecimal value, then just type it in. If you have a string that is converted to hex, prefix the key with a lowercase s and a colon. Once you've entered the key, save the file and close the text editor. Enter this command to restart the networking daemon with the changes to that configuration file.
```
sudo /etc/init.d/networking restart
```
From here you can start connectivity testing with utilities like ping and traceroute.

---


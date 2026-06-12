---
title: "Connect to WEP encrypted wireless network"
date: 2006-01-16
forum: General Help
---

### Post by PMO6022 on 2006-01-16
I am trying to connect to a WEP encrypted wireless network without much luck. I have a working Intel wireless 2200BG card. I can connect to the network when I disable the wep security. With the security enabled, I can not connect, however. 
 
I would very much perfer to do this from the command line. Here is what I have tried:```
sudo iwconfig eth1 essid <essid_of_router> key <10_digit_hex_key_from_router_setup_page>
sudo ifup eth1
```which gives me a series of DHCPDISCOVER messages then fails to connect.  
 
Any ideas?

---

### Post by Azion on 2006-01-16
I'm using a netgear, works fine without encryption, but I can't get it to work with it either

---

### Post by lnxpwr on 2006-01-16
how do you enter the key ? just type it without any special character"-" 

sudo iwconfig eth1 mode managed essid <my_essid> key <0123456789>
sudo dhclient eth1

..works for me

---

### Post by joplass on 2006-01-16
I am using a Linksys 54WPC card with a Linksys 54WRT router and WEP works great.  I wouldn't know where to start and provide you guys the help you seek.  Maybe it has to do with the way you set up the whole thing.  During my set up I did not use the command line at all.  I installed ndiswraper-utils and ndisgtk using Synaptic from there I got Windows Wireless Drivers; I used this gui to installed the driver right from the card software CDRom.

---

### Post by soulestream on 2006-01-16
/etc/network/interfaces

# The primary network interface
iface eth1 inet static
	address 192.168.1.105
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid YOURSSID
	wireless-key1 FFFFFFFFFFFFFFFFFFFFFFF  <-ENTER YOUR KEY HERE
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 65.24.7.3
	wireless-key FFFFFFFFFFFFFFFFFFFFFFFFFF <-MINE IS HERE TOO FOR SOME REASON
	Missed beacon:0
	Power Management: off


this is for a static setup, but I hope it helps

soule

---

### Post by joplass on 2006-01-16
[QUOTE=PMO6022]I am trying to connect to a WEP encrypted wireless network without much luck. I have a working Intel wireless 2200BG card. I can connect to the network when I disable the wep security. With the security enabled, I can not connect, however. 
 
I would very much perfer to do this from the command line. Here is what I have tried:```
sudo iwconfig eth1 essid <essid_of_router> key <10_digit_hex_key_from_router_setup_page>
sudo ifup eth1
```which gives me a series of DHCPDISCOVER messages then fails to connect.  
 
Any ideas?[/QUOTE]

By the way isn't your wireless supposed to appear as wlan0 instead of eth1?:confused:

---

### Post by soulestream on 2006-01-16
> By the way isn't your wireless supposed to appear as wlan0 instead of eth1?

eth, ath, wlan

depends on the card/driver

soule

---

### Post by lnxpwr on 2006-01-16
with iwconfig: using a hex key just type XXXXXXXXXX. if your key is an ascii string use the prefix   <s: >    before the key!

---

### Post by PMO6022 on 2006-01-16
thanks guys for all of your suggestions, but I am still not able to get it to work. I am actually doing this at a friend's house because I don't have a wireless network at home. I am using his (windows) laptop connected through the network to post this, so the router seems fine. 
 
I'm getting pretty frustrated with this right now, so I may have to walk away and try again later. If anyone has any useful links I'd appreciate it. That way I can read up for my next crack at this.

---

### Post by jago25_98 on 2006-01-16
I have same problem :/

Try:
```

iwlist scanning

```

Mine doesn't find any networks when it should, which I should find significant yes?

---

### Post by soulestream on 2006-01-16
also you may want to go to System -> administration -> networking 

and make sure its active

or use ifconfig eth1 up

soule

---


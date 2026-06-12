---
title: "My Wii wants to talk to my PC!"
date: 2009-03-31
forum: General Help
---

### Post by Kevbert on 2009-03-31
I have a router which has a number of devices connect to it including a Wii console. The router is set to only allow four devices to connect to it via the MAC addresses.
I've been running
```
sudo tcpdump -i wlan0 > tcpdump.txt
```
to save all data from and to my desktop PC to a text file. In this file I get things like
```
14:29:30.282202 00:10:20:30:40:50 (oui Unknown) Unknown SSAP 0x20 > **00:11:22:33:44:55** (oui Unknown) Null Supervisory, Receiver not Ready, rcv seq 16, Flags [Command], length 166
14:29:30.543805 00:10:20:30:40:50 (oui Unknown) Unknown SSAP 0x20 > **00:11:22:33:44:55** (oui Unknown) Null Information, send seq 3, rcv seq 16, Flags [Command], length 76
```
The second MAC code shown in bold is my Wii console (MAC codes changed for security reasons from actual codes). Funnily enough oui (in French) sounds like Wii (just co-incidence). Is there any way to hide my Wii from the PC ?
This may not seem trivial, but further down the logs I get what looks like some columns of hex programming with a far right column of ASCII characters.  This looks like data is being passed between the Wii and the wireless adapter on my PC:
```
15:52:13.919097 00:10:20:30:40:50 (oui Unknown) > 00:11:22:33:44:55 (oui Unknown), ethertype Unknown (0x05f8), length 1542: 
	0x0000:  0020 0d20 0000 0000 16c8 4f4a fb7b a3f6  ..........OJ.{..
	0x0010:  ac01 00c2 05f0 87c5 1636 100a b5eb 23e8  .........6....#.
	0x0020:  bbba f143 22d2 54c9 d90a ed98 2f45 333b  ...C".T...../E3;
	0x0030:  8be0 e1ed 0e2c 55a5 7cb2 8427 b719 44cb  .....,T.|..'..D.
	0x0040:  f446 b814 feea 2e25 5319 3bdc 57dc e775  .F.....%S.;.W..u
	0x0050:  d080                                     .y

``` 
Comments...

---

### Post by Kevbert on 2009-05-13
Bump... anyone ?

---

### Post by Bark on 2009-05-13
1

---


---
title: "H169 on dodo network on ubuntu 8.10"
date: 2009-04-26
forum: General Help
---

### Post by kingswood71 on 2009-04-26
hope this helps...
Connection H169 modem to Dodo network in Australia on 8.1

1.plug the usb in.
2.network manager will see it as an E622.
3.Select next etc.
4.select optus 3G
5.itw ill try to connect but cant.
6.Open up edit connections.
7.Mobile broadband, optus 3G edit connections
8.in APN type dodolns1
9.in the PPP tab, select Pap only, then select auto connect. Apply.
10.It will now connect.
11.You most likely will not be able to get firefox to work, so...
12. open up edit connections again and delete and DNS numbers in the ipv4 setting.
13.Open up a terminal and type..  sudo gedit /etc/resolv.conf
14.delete the DNS numbers there and replace with 208.67.222.222 and 208.67.220.220.
15.save this.
16.Now disable ipv6. Open a terminal and type sudo gedit /etc/modprobe.d/aliases
17.find the ipv6 line and type off before the ipv6.
18.Now new terminal and type sudo gedit /etc/modprobe.d/blacklist
19.type in blacklist ipv6 , #ipv6 and ipv6 off.
20.Save this.
21.For extra surety, open new terminal then type. Sudo gedit /etc/modprobe.d/bad_list
22.add to bad list #ipv6, ipv6 and ipv6 off.
23.Save file.
24.Reboot computer.

This should work...worked for me!

Good luck
Rohan

---


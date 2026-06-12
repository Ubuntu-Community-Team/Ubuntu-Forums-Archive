---
title: "Configure Ethernet Card"
date: 2008-12-04
forum: Desktop Environments
---

### Post by sharathpaps on 2008-12-04
Hi,
           I've just installed Ubuntu 8.10 & my Ethernet 10/100 Mbps card is supported by the OS. But I am not able to configure it to connect to the internet. I use a Cable 384 Kbps Connection with DHCP. I usually have to set the card to obtain the IP address & the DNS Servers from my ISP. 

How can I configure my card to connect to the Internet?

Thank You

{I am a NOOB}

---

### Post by lequytuan on 2008-12-04
you can configure NIC via file /etc/network/interfaces . 

Ex: sudo nano /etc/network/interfaces

And configure DNS via file resolv.conf 
ex: sudo nano /etc/resolv.conf.

---

### Post by sharathpaps on 2008-12-04
@ lequytuan

thanx...  dont have any idea abt what actually configuring will do...I'll open these files from a terminal & see what I can do..

---

### Post by sharathpaps on 2008-12-04
@ lequytuan

thanx...  dont have any idea abt what actually configuring will do...I'll open these files from a terminal & see what I can do..

---

### Post by Zorael on 2008-12-04
Doesn't the NetworkManager applet do the trick for you? The one in the tray manager on the panel, by the clock?

---

### Post by sharathpaps on 2008-12-04
@ Zorael

I tried that...I actually managed to get a message saying "Local Area Network Connected" or something to that effect. But then it disconnected itself again. Happened more than one time. I am beginning to think that my ISP needs to do something to get things going...

And...sorry for the earlier double post. I tried to delete it but couldn't..

---


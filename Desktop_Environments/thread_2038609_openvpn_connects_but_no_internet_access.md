---
title: "openvpn connects but no internet access"
date: 2012-08-07
forum: Desktop Environments
---

### Post by ark1-87 on 2012-08-07
Hello, sorry if i have posted in the wrong area but this is where it said to post on the Xubuntu help and support site please move if inappropriate.

 I have openVPN installed on my VPS server which is debian 6 through following the linode [http://library.linode.com/networking/openvpn/debian-6-squeeze](http://library.linode.com/networking/openvpn/debian-6-squeeze) documentation. The whole guide was followed including the tunneling and dnsmasq part. 
From my client machine I can connect to the VPN but then I do not have any internet accesss. 
 I use the client.conf to connect to the vpn and followed steps 10 and 11 from this guide: [http://tipupdate.com/how-to-install-ope](http://tipupdate.com/how-to-install-ope) ... buntu-vps/ 
My friend who can connect to the VPN, has internet access, and pulls the IP from linode on whatismyipaddress.com. I am using almost the same distro as he is using ubuntu 12.04 and i am using xubuntu 12.04 64bit.
I asked in the linode IRC chat and I kept getting responses to check my routing and NAT forwarding. I think the problem might be client-side related since my friend is able to connect with his certs which are different than the ones I am using.

---

### Post by ark1-87 on 2012-08-09
got it to work, thanks anyways..

added:

iptables -A INPUT -j ACCEPT -s 10.8.0.0/24 -p esp
iptables -A INPUT -j ACCEPT -s 10.8.0.0/24 -p udp -m multiport --sports isakmp,10000
iptables -A INPUT -j ACCEPT -i tun+
iptables -A OUTPUT -j ACCEPT -d 10.8.0.0/24 -p esp
iptables -A OUTPUT -j ACCEPT -d 10.8.0.0/24 -p udp -m multiport --dports isakmp,10000
iptables -A OUTPUT -j ACCEPT -o tun+

to: /etc/firestarter/user-pre

---


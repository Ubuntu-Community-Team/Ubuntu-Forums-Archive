---
title: "How do I connect to virtual /var/www from windows?"
date: 2006-11-22
forum: Desktop Environments
---

### Post by sim-x on 2006-11-22
Hi Guys,

I have installed ubuntu server using vmware player on my windows box. I installed apache2 on the virtual server. How do I access the /var/www folder that is on my virtual server from a web browser on the windows box WITHOUT connecting to internet?

Many thanks,

sim-x
seattle, wa

---

### Post by chrisccoulson on 2006-11-23
I run Windows XP in a virtual machine from within Dapper. For sharing files between the 2, I set up a Samba share. I'm not aware of any other way of sharing files between host and guest.

---

### Post by sim-x on 2006-11-24
Thanks,
But I'm not looking to share files per se. I have installed mediawiki on my virtual server, and I would like to access it using the web browser. This works fine when my machine is connected to a LAN coz all i have to do is type the IP of the virtual server as the url and voila

but is there a way to do this when NO internet connection is present?

---

### Post by pveith on 2006-11-24
This isn't an ubuntu question. Please lookup "host-only network setup" in the vmware docs. The configuration is done with the selection of the network adapter done before actually installing the guest. You might try to shut down the guest, add a host only network card to the guest and startup your ubuntu-server (Usually a briged-network card is installed. At least with the ubuntu-demo image, which vmware.com provides.) Then you should be able to configure the new device. Haven't tested it so. And you should switch from vmware-player to vmware-server, which also does not cost anything except your email registratioon on vmware.com. (Link:[http://www.vmware.com/products/server/](http://www.vmware.com/products/server/) )

Hope this helps...

---

### Post by mark_g on 2006-11-25
I have done this just yesterday. Here's how it's done:

1. service iptables stop

2. Set VMWare networkconnection (Ethernet) as NAT

3. VMware Network Adapter VMnet8:

e.g. 192.168.80.1 mask 255.255.255.0

4. Linux ip 192.168.80.2  mask 255.255.255.0


5. Restart network: sudo /etc/init.d/network restart

6. You can now connect to 192.168.80.2

---

### Post by sim-x on 2006-11-27
Thanks! Although a few problems:

<1. service iptables stop

I get "-bash: service: command not found"


<2. Set VMWare networkconnection (Ethernet) as NAT

How do I do that?


<3. VMware Network Adapter VMnet8:

e.g. 192.168.80.1 mask 255.255.255.0    OK!

4. Linux ip 192.168.80.2 mask 255.255.255.0  OK!

making sure there is no typo though: .1 on VMnet8 and .2 in /etc/network/interfaces

I appreciate you help :)

---

### Post by mark_g on 2006-11-29
<1. service iptables stop

I get "-bash: service: command not found"

My mistake, that's how to stop the firewall on Fedora (I run Fedora in VMWare). You only have to stop this if you run it of course. You can check by running "ps aux | grep iptables".

<2. Set VMWare networkconnection (Ethernet) as NAT

If you right-click on the tab of your loaded OS in VMWare _Workstation_, you can select this option in "Settings" > "Ethernet1". Don't know if this is possible in VMWare Player though.

4. Linux ip 192.168.80.2 mask 255.255.255.0 OK!

making sure there is no typo though: .1 on VMnet8 and .2 in /etc/network/interfaces

The IP-addresses aren't that important as long as they are private and in the same subnet. Instead of editing /etc/network/interfaces, you could also use the command

```
sudo ifconfig vmnet8 192.168.80.2 netmask 255.255.255.0
```

---


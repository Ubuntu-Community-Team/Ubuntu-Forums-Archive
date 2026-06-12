---
title: "Printing to hostname instead of ip-address does not work"
date: 2009-01-20
forum: General Help
---

### Post by breaky9973 on 2009-01-20
Here at work i have set up a workgroup with one windows 2003 server with internet connectiong sharing enabled thus acting as a DHCP server. The clients are installed with a mixed configuration of Windows XP, Vista and one Ubuntu 8.10 (Which I am using now).

Also on the network is a HP Laserjet 3055 MFC. This one is directly connected to the network.

Now here comes my problem:

On the Windows XP/Vista clients I installed this printer as a local printer and created at TCP/IP port. The Windows clients print directly to the hostname of the printer, regardless what kind of ip-address is assigned.

In Ubuntu I cannot seem to get this to work. Ubuntu finds the printer and i can print to it but whenever it's ip-address changes i have to re-scan for the printer again. 

I tried to set it up via AppSocket/HP Jetdirect so i can print to the hostname instead of an ip-address but that won't work too.

One thing more:

In Windows i can ping for the hostname of the printer....in Ubuntu not. 

My guess it is a networking issue but who can help me further?

---

### Post by cmnorton on 2009-01-20
Is the printer's IP address static or reserved in DHCP. If not it should be. Please remember in Windows you are using WINS (probably using) name resolution. 

I have a semi-permanent laptop that acts as a low-powered Ubuntu server, but it also has to travel. So, in my office's sub-net where the laptop can behave like a server, I have a DHCP-reserved address.

---

### Post by Liviu-Theodor on 2009-01-20
Yes, the printer should have static IP. We have a similar setup here, with Fedora servers and Vista workstations (two of them transformed into Ubuntu workstations), with a Lexmark printer connected directly to the network, having static IP adress. I can print from Ubuntu without problems. Neither Windows should have any problem detecting it with static IP address. Our setup is declaring the printer IP adress with 1 bigger than that of the server.

---

### Post by breaky9973 on 2009-01-20
The printer is setup as DHCP. I could assign a static ip-address to the printer and that would probably solve my problem.

For me however, I want to use the printer with DHCP. This is more or less as a test because we want to use Ubuntu on a much larger network. This will involve much more computers and multiple networked printers and I prefer DHCP instead of assigning static ip-addresses. In a way I need to convince my partners that we can use Ubuntu with as little tweaking to the network as possible.

---

### Post by Liviu-Theodor on 2009-01-20
I said use static IP adress with the network printer, I mean just for it. For the ubuntu station(s) you should use dynamic adress(es).

---

### Post by breaky9973 on 2009-01-20
The printer is now configured as DHCP. I don't like to use a static IP address for the printers as I have to convince the other network admin's to use Ubuntu with as little tweaking to the network as possible.

---

### Post by monkeyking on 2009-01-20
Can you ping the printer from ubuntu using it's ip adr?
Does it work if you add the printer to your hosts?

ping uses icmp, maybe the win ping utility caches the wins resolution.

---

### Post by breaky9973 on 2009-01-20
Pinging the printer works. If i add the hostname of the printer with the current ip-address to the hosts file it works also. But how do i add a printer to hosts without specifying an ip-address? 

WINS on the server is disabled (Just checked). If i print out a network configuration page from the printer it also lists the WINS Server as 0.0.0.0

---

### Post by cmnorton on 2009-01-20
> **breaky9973 said:**
> Pinging the printer works. If i add the hostname of the printer with the current ip-address to the hosts file it works also. But how do i add a printer to hosts without specifying an ip-address? 

WINS on the server is disabled (Just checked). If i print out a network configuration page from the printer it also lists the WINS Server as 0.0.0.0

You cannot add a printer to hosts without an IP address. Is this printer connected to a system, or is this printer a network printer? Either way, its IP address needs to be static.

---

### Post by breaky9973 on 2009-01-20
This printer is a network printer. It is connected to a switch. The Windows 2003 server is set up to take care of DHCP and DNS and act as a fileserver. 

But just let me get this straight: Windows clients can print to a network printer (which gets its ip from DHCP and not static) just by specifying the hostname and Ubuntu clients cannot? That would be a real bummer....

The ultimate goal is to almost seamlessly integrate Ubuntu into a big corporate network. And in this network there are about 110 networked printers, all which have an ip-address assigned by DHCP.

---

### Post by dcstar on 2009-01-20
> **breaky9973 said:**
> This printer is a network printer. It is connected to a switch. The Windows 2003 server is set up to take care of DHCP and DNS and act as a fileserver. 

But just let me get this straight: Windows clients can print to a network printer (which gets its ip from DHCP and not static) just by specifying the hostname and Ubuntu clients cannot? That would be a real bummer....

The ultimate goal is to almost seamlessly integrate Ubuntu into a big corporate network. And in this network there are about 110 networked printers, all which have an ip-address assigned by DHCP.

If you have set up Ubuntu to use DHCP it will get the DNS entry from the DHCP server, **that** is what you have to set up correctly.

---

### Post by breaky9973 on 2009-01-20
Ok I will check DNS on the server. 

I did some looking around and it looks like HP Jetdirects also communicate via SNMP. I just now installed SNMP on my client and when I am on the office i will try again.

---

### Post by dcstar on 2009-01-20
> **breaky9973 said:**
> Ok I will check DNS on the server. 
.....

Your internal DNS server should be set up as the only DNS server for clients, if it allocates IP addresses it should have all your network resources in it (either automatically or manually) so the clients can access it. If it is a WINS server then that should also be in the DHCP packet sent to clients.

Ubuntu clients can only work with the information/resources your network gives them.

---

### Post by breaky9973 on 2009-01-21
Ok a traceroute (from the Ubuntu client) with the ip address from the printer solved the problem. The solution is so simple that I just want to bump my head.

Just typing in the hostname like in a Windows client is not enough. In this case i also needed to add .local after the hostname (<hostname>.local) and then everything worked like a charm.

Thanks everyone for your great suggestions. :-)

---


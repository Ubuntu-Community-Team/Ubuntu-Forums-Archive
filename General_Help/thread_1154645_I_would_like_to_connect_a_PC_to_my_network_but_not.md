---
title: "I would like to connect a PC to my network but not the internet..."
date: 2009-05-10
forum: General Help
---

### Post by toejamfootball on 2009-05-10
I have two Linux Desktops and one XP Desktop. I use Desktop 1 for Web browsing and it acts as a storage server. I use the Desktop 2 to stream from Desktop 1 to the TV.

My XP PC has stayed offline except for a couple of Product registrations. I would like to have it access the network (so I can access the storage of Desktop 1) but I do not want it to actually be connected to the internet.

How would I go about doing this? I know about Samba and will use that for the FTP etc. but I am unsure about how to keep XP from recognising that it is online. Would I use a firewall or is it possible to just disable the internet connection but still use samba?

That probably doesn't make sense, hopefully someone understands!

Cheers!

---

### Post by mb_webguy on 2009-05-10
I'd go the firewall route.  If all you want is to share files via Samba, block everything on that computer but UDP on port 445.

---

### Post by toejamfootball on 2009-05-10
> **mb_webguy said:**
> I'd go the firewall route.  If all you want is to share files via Samba, block everything on that computer but UDP on port 445.
I got some help from somewhere else, and have just put this into place. Using the Router.

Thanks mate.

---

### Post by Hobgoblin on 2009-05-10
The information you have left out, and possibly the key to this is how do you connect to the internet?

---

### Post by 3rdalbum on 2009-05-10
It's been a long time since I've used XP, but this may work:

Set up the XP machine to use a static network configuration rather than DHCP. Assign it an IP address in your local network (something like 192.168.0.12), and do not enter anything for "gateway" or "DNS".

Without the address of the gateway (which is actually the bit of the router that can send requests to the Internet), XP will not be able to connect to the internet. But it will be able to still use resources on the local network.

---

### Post by tkelito on 2009-05-10
> **3rdalbum said:**
> It's been a long time since I've used XP, but this may work:

Set up the XP machine to use a static network configuration rather than DHCP. Assign it an IP address in your local network (something like 192.168.0.12), and do not enter anything for "gateway" or "DNS".

Without the address of the gateway (which is actually the bit of the router that can send requests to the Internet), XP will not be able to connect to the internet. But it will be able to still use resources on the local network.

He is 100% correct, I have a Desktop that functions as a multimedia server.  The Wireless 300Mb/s connection has DNS servers entered along with a Static IP and it connects online while it's second connection is lacking DNS servers and it only connects to the LAN to share the multimedia via 1Gb/s connection.

Wireless (Internet & LAN):

192.168.1.2
255.255.255.0
192.168.1.1
xx.xx.xxx.xx <- Enter your
xx.xx.xxx.xx <- DNS Servers

Wired (LAN):

192.168.0.2
255.255.255.0
192.168.0.1
00.00.000.00 <- Leave blank or
00.00.000.00 <- use 0's

-tkelito

---

### Post by toejamfootball on 2009-05-10
Thanks guys, this works. :)

---

### Post by 3rdalbum on 2009-05-10
> **tkelito said:**
> it's second connection is lacking DNS servers and it only connects to the LAN to share the multimedia via 1Gb/s connection.

This would work quite well as everything uses domain names rather than IP addresses (for instance, Microsoft Update will connect to something like "windowsupdate.microsoft.com" rather than directly to "142.35.67.189"). But theoretically, any service that communicates directly using IP addresses would still be able to get through. That's why I advised to omit the gateway. Without the gateway address, no packets can reach the internet.

---

### Post by toejamfootball on 2009-05-10
I have got it all working pretty well now. I just need to be able to acces the XP computer from my Linux machines. I can't seem to be able to do this?

I have tried the same method I use to transfer files between Linux and Mac machines, using OpenSSH, but cannot get through....

Any ideas?

---

### Post by Hobgoblin on 2009-05-10
Windows doesn't have SSH built in, the easiest way might be to enable file and printer sharing on the XP system then use samba on the Linux boxes.

---


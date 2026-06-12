---
title: "Assign an IP???"
date: 2005-12-21
forum: General Help
---

### Post by Tux_Phoenix on 2005-12-21
Ok I have been looking around for a while now and cann't figure out how to assign an ip to my ubuntu install.  I don't have gnome running it is going to be a server.  I have apache installed and my router forwarding port 80 but now I need to set the ip of the server.  Can someone point me in the right direction. I am sure it is some easy config file or something like that.


Thanks

---

### Post by schilcha on 2005-12-21
Ethernet-configuration can be found in /etc/network/interfaces. There's also a man-page for it (man interfaces) with good examples.

Hope it helps...

---

### Post by alamba on 2005-12-21
Another way:

ifconfig eth0 192.168.0.1

substitute eth0 for your interface and the IP as per your needs.

Akshay

---

### Post by Gowator on 2005-12-21
The method above changes the IP for the time its up buit it will not have one assigned if you reboot.  

If you are not using a GUI and hence no network tool then you need to change /etc/network/inteferfaces

 iface eth0  inet static
                   address 192.168.1.1
                   netmask 255.255.255

This is a RFC non routable (internal) address if you have a fixe3d IP you use that.  
If you have a DHCP server then 
 iface eth0 inet dhcp
                   

see "man interfaces" for more info

---

### Post by Tux_Phoenix on 2005-12-21
Awsome thanks for the help.  I set the ip on the server but now I seem to be having anouther problem.  This one with the routing to the server.  I have a dsl modem connected to a 4 port router connected to a 12 port switch.  

Ok on the modem I have all port 80 traffic going to 10.0.0.5 so on the router I set it to atatic ip and gave it the ip 10.0.0.5 . 

Then on the router I have it set to send all port 80 traffic to 192.168.1.32 (the ip I gave my server).  I just wanted to make sure I did all that right.  For some reason when I try to connect to the static Ip my ISP gave me it goes to the log in for my modem instead of forwarding the traffic.  Anyideas on things I should check?  Thanks.

---

### Post by Gowator on 2005-12-22
[QUOTE=Tux_Phoenix]Awsome thanks for the help.  I set the ip on the server but now I seem to be having anouther problem.  This one with the routing to the server.  I have a dsl modem connected to a 4 port router connected to a 12 port switch.  

Ok on the modem I have all port 80 traffic going to 10.0.0.5 so on the router I set it to atatic ip and gave it the ip 10.0.0.5 . 

Then on the router I have it set to send all port 80 traffic to 192.168.1.32 (the ip I gave my server).  I just wanted to make sure I did all that right.  For some reason when I try to connect to the static Ip my ISP gave me it goes to the log in for my modem instead of forwarding the traffic.  Anyideas on things I should check?  Thanks.[/QUOTE]

You need to set the default route.  
route add default gw 192.168.1.x  (x is the internal IP of the router ... probably 1) which I am assuming is running NAT and has an external address 10.0.0.x ....  which connects to the modem which has an internal 10.0.0.5 and external the IP range of your ISP....  
you might be over complicating this!

---


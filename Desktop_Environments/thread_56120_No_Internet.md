---
title: "No Internet"
date: 2005-08-11
forum: Desktop Environments
---

### Post by SaCeR on 2005-08-11
I have a problem when im at my school.. they have both wired and wireless network.. but when i connect to them, it won't allow me to go on the internet.. but i can see the network...
I tried to ask the administrator but he had no ideer why.. 
i have tried with windows and fedora... it worked fine... anyone who can help me =|?

---

### Post by varunus on 2005-08-11
It worked with both windows and fedora?  Then it should work with Ubuntu.

What steps did you take to try and make it work?  Did you open System->Administration->Networking and configure your wireless and ethernet?  What config options did you use?  Do you get an IP address?

Try deactivating one and activating the other, see if only having one active makes it work...

Can you post the output of ifconfig and iwconfig in a terminal after you plug in the cable/connect to the wireless?

---

### Post by camp on 2005-08-11
Hi SaCeR,

That sounds really weird!? are you sure that your NIC is really working fine?
Do you have an IP and can you access anything else on the network? Try to print on a printer on the network or something, why not getting some files from a file server.

Also check, if you are using dual boot, if you get the same IP address on both OS. As I understand, this only happens when using Ubuntu?

Have you done anything to your ubuntu configuration? or is it a stragith vanilla setup?

Have a nice day!
/Camp

---

### Post by SaCeR on 2005-08-11
Yes it does sound very very weird.. and both my wired and wireless works fine... im jusing it at home and ad a friend... no problem there...
I did get an IP, and i could access the users on the network...

i have tried both activation and deactivation the wired and wireless, i have used DHTP and Static IP.... i tried one of my friends IP and gateway and stuff...

but it would not ping the school's servers that was located on x.x.x.1 and x.x.x.2, but i could ping other on the network...

---

### Post by varunus on 2005-08-11
Can you copy over the DNS server information from windows into Ubuntu?  You also may need to add the correct search domain.  (These are found in DNS tab in System->Administration->Networking in Ubuntu, and in Windows properties dialog for the network connection; select TCP/IP and click properties, then click advanced, there's a DNS tab; It has a search domain and DNS servers.)

Its very strange that this worked in Fedora and not in Ubuntu...but if its working in Windows, you can get it to work.  I'd recommend using DHCP if the network is supposed to be DHCP, and make sure the DNS gets correctly detected...also, can you post the output of ifconfig and iwconfig here after you try to connect?  Also the output of route -n.

---

### Post by SaCeR on 2005-08-11
[QUOTE=varunus]Can you copy over the DNS server information from windows into Ubuntu?  You also may need to add the correct search domain.  (These are found in DNS tab in System->Administration->Networking in Ubuntu, and in Windows properties dialog for the network connection; select TCP/IP and click properties, then click advanced, there's a DNS tab; It has a search domain and DNS servers.)

Its very strange that this worked in Fedora and not in Ubuntu...but if its working in Windows, you can get it to work.  I'd recommend using DHCP if the network is supposed to be DHCP, and make sure the DNS gets correctly detected...also, can you post the output of ifconfig and iwconfig here after you try to connect?  Also the output of route -n.[/QUOTE]
 I does support DHCP... and im getting the right DNS.. but i can try to give you the ifconfig and iwconfig and the route -n...

---

### Post by celloandy on 2005-08-11
I have a bit of a hunch about this one... try executing the following command as root:

```
echo 0 > /proc/sys/net/ipv4/tcp_default_win_scale
```

And then try accessing your network again.  Does that make it work?

Andrew

---

### Post by SaCeR on 2005-08-17
[QUOTE=celloandy]I have a bit of a hunch about this one... try executing the following command as root:

```
echo 0 > /proc/sys/net/ipv4/tcp_default_win_scale
```

And then try accessing your network again.  Does that make it work?

Andrew[/QUOTE]


 Just tryed... There is no file like that :| ....

---

### Post by SaCeR on 2005-08-17
[QUOTE=varunus]Can you copy over the DNS server information from windows into Ubuntu?  You also may need to add the correct search domain.  (These are found in DNS tab in System->Administration->Networking in Ubuntu, and in Windows properties dialog for the network connection; select TCP/IP and click properties, then click advanced, there's a DNS tab; It has a search domain and DNS servers.)

Its very strange that this worked in Fedora and not in Ubuntu...but if its working in Windows, you can get it to work.  I'd recommend using DHCP if the network is supposed to be DHCP, and make sure the DNS gets correctly detected...also, can you post the output of ifconfig and iwconfig here after you try to connect?  Also the output of route -n.[/QUOTE]

ifconfig:

eth1

     ......
      inet addr: 172.27.73.192    Bcast:172.27.75.255   Mask: 255.255.252.0
      inet6 addr: fe80::20e:35ff:fe6f:334c/64   Scope: Link
      UP BROADCAST RUNNING MULTICAST     MTU: 1500 Metric: 1
      ......

route -n:

Kernel IP routing table
Destination      Gateway   Genmask:                    Flags:   Metric:  Ref: Use:   Iface:
172.27.72.0      0.0.0.0       255.255.252.0                U          0        0     0        eth1

---

### Post by Teren on 2005-08-17
[QUOTE=SaCeR]ifconfig:

eth1

     ......
      inet addr: 172.27.73.192    Bcast:172.27.75.255   Mask: 255.255.252.0
      inet6 addr: fe80::20e:35ff:fe6f:334c/64   Scope: Link
      UP BROADCAST RUNNING MULTICAST     MTU: 1500 Metric: 1
      ......

route -n:

Kernel IP routing table
Destination      Gateway   Genmask:                    Flags:   Metric:  Ref: Use:   Iface:
172.27.72.0      0.0.0.0       255.255.252.0                U          0        0     0        eth1[/QUOTE]
 you have no default gateway

$ route add default gw <ip>

<ip> is prolly 172.27.72.1

---

### Post by SaCeR on 2005-08-18
[QUOTE=Teren]you have no default gateway

$ route add default gw <ip>

<ip> is prolly 172.27.72.1[/QUOTE]
 ... i can write it, but it does not help... i ask the administator, and the DHCP server is at 172.27.77.1, but then i enter that ip address it can't find the server... i have not installed any firewall myself...

---

### Post by SaCeR on 2005-08-18
Anyone :|? I Really need help at this =/

---

### Post by celloandy on 2005-08-18
[QUOTE=SaCeR]Just tryed... There is no file like that :| ....[/QUOTE]

Sorry, it seems they've renamed the file in more recent kernel versions.  Should now be:


echo 0 > /proc/sys/net/ipv4/tcp_window_scaling

---

### Post by SaCeR on 2005-08-19
[QUOTE=celloandy]Sorry, it seems they've renamed the file in more recent kernel versions.  Should now be:


echo 0 > /proc/sys/net/ipv4/tcp_window_scaling[/QUOTE]

i tried today.. nothing happend..  another mate who has ubuntu installed, ented static IP and set the gateway to 172.27.77.1 (the schools gateway(DHCP sever))... he got on the internet, but when he turn the computer off and started it again he can't get on again.. can i be something to do with the firewall... i have not checked.. and i did not chance anything, from the begging when i installed ubuntu.. :| i can't even ping te DHCP server... =/

---

### Post by heimo on 2005-08-20
Something you could try. Put this into your /etc/network/interfaces file:
 ```
auto lo
iface lo inet loopback

mapping hotplug
		script grep
		map eth1

iface eth1 inet dhcp

``` 

And run:
 ```
sudo /etc/init.d/networking restart
sudo dhclient eth1
ifconfig eth1
route -n

``` 

What happens?

---

### Post by SaCeR on 2005-08-22
[QUOTE=heimo]Something you could try. Put this into your /etc/network/interfaces file:
 ```
auto lo
iface lo inet loopback

mapping hotplug
		script grep
		map eth1

iface eth1 inet dhcp

``` 

And run:
 ```
sudo /etc/init.d/networking restart
sudo dhclient eth1
ifconfig eth1
route -n

``` 

What happens?[/QUOTE]
 hmm.. there is no different then before... there is still no gateway and i can see the users on the network.. :|

---

### Post by heimo on 2005-08-22
Add line 'gateway *gatewayIP' *after line with eth1 in /etc/network/interfaces, restart networking, run route -n (check that gateway is there), try pinging gw.

---

### Post by SaCeR on 2005-08-23
[QUOTE=heimo]Add line 'gateway *gatewayIP' *after line with eth1 in /etc/network/interfaces, restart networking, run route -n (check that gateway is there), try pinging gw.[/QUOTE]
 tryed... same thing :|

---


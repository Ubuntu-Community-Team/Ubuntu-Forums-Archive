---
title: "Need help enabling networking"
date: 2006-09-24
forum: Desktop Environments
---

### Post by 2pacalypse on 2006-09-24
Hi Everybody ;)

My Sister install Ubuntu Dapper Drake on her System today but unfortunatly theres a minor problem that prevents her from using ubuntu well. the problem is that she cant see the network and hence cannot connect to the internet. her computer has a Realtek PCI 10/100 Fast Ethernet which Ubuntu recongizes as eth0 but it does seem to work correctly she cant see the network at all and theres no network traffic from her computer at all. we tried to download two drivers from [the Realtek driver download site](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=6&Level=5&Conn=4&DownTypeID=3&GetDown=false#7) (named Packet driver & Linux driver for kernel 2.4.x (RedHat 7.2/ 7.3/ 8.0/ 9.0)) but both didnt worked, the Packet driver has some Exe file in there and the Kernel 2.4.x refuses to be installed (i tried to use the .configure / .make commands but nothin happends) does any1 know how to make the network adapter work properly?

Edit: were sure that the prob is not in the hardware it self or the cable cuz of Windows the network works fine

---

### Post by got_nix on 2006-09-24
seems your sisters card isn't the most linux compatible ethernet card.. you can try editing your menu.lst file and adding this

"noapic acpi=off"

file location /boot/grub/menu.lst use gedit or vi as sudo user.

---

### Post by 2pacalypse on 2006-09-24
My sisters card should be compatible with Linux, after all why would there be linux drivers for it if it wasnt...

about the noapic acpi=off, i am unsure about what part i should place it in so i picked a random one... ill edit this post when i get the result

EDIT: the noapic thingy didnt change a thing

---

### Post by got_nix on 2006-09-24
The location shouldn't matter at all.. so i guess it didn't help you.. i saw a guy do that for a debian setup and since ubuntu is debian based i figure it might work for you.

---

### Post by Ramses de Norre on 2006-09-24
If eth0 is there the driver should be ok, what's the content of /etc/network/interfaces?
And what's your network setup? DHCP or static and could you give some stuff like the IP (if static) the standard gateway and subnetmask and so on..

---

### Post by 2pacalypse on 2006-09-24
well, if it worked on Debian most odds are that it will run on ubuntu. anyway i've been looking into the file abit and i noticed that

a- it hasnt been updated from the year 2003
b- the most recent Kernel Version it supports is 2.4.x, and since ubuntu Dapper Drake has a Kernel Version 2.6.15 the driver is non supported.

those two thingies are the most probably reason for the problem. can any1 give me any tips on how to fix this little problem, maybe direct me to some place where i can find a driver that supports Kernel version 2.6.15 or some bypass for the driver?

EDIT:

The eth0 is set on DHCP and the default gateway is somewhat problematic to say because when i run the Networking Setting Program the default gateway is blank but no matter how many times i've changed it, its always resetting back to blank

the /etc/network/inteface gave me this:

```

auto lo
inface lo inety loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

---

### Post by Ramses de Norre on 2006-09-24
So you're sure it's eth0 you need? In that case comment out all sections except those for eth0 and lo.
Then: are you able to connect with another device to your network using dhcp? (to make sure the dhcp server is setup correctely).
If I'm right it's a wired connection, yes?
What's the output of 
```
sudo ifconfig eth0
sudo ifup eth0
sudo ifdown eth0 && sleep 10 && sudo ifup eth0
```

---

### Post by 2pacalypse on 2006-09-24
ok, i deleted all the other things in the list (left only eth0 and lo), i dont know what is DHCP but i presume its my router and since im writing here ok then i guess its working. and now the results for the code

```

sudo ifconfig eth0
-------------------
Link encap:Ethernet HWouddr 00:E0:4D:15:43:13
inet6 addr: fe80:2eo:4dff:fe15:4313/64 scape link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX Packets : 3 errors : 0 dropped : 0 overruns : 0 frame : 0
TX Packets : 3 errors : 0 dropped : 0 overruns : 0 carrier : 0
RX Bytes" 741 (744.0b) FX Bytes 8802 (8.5KiB)
Interrupt : 11 Base Adress 0x8000

sudo ifup eth0
--------------
ifup: interfact eth0 already configured

sudo ifdown eth0 && sleep 10 && sudo ifup eth0
-----------------------------------------------
Internet Sytstem Consortium DHCP Client V3.03
Copyright 2004-2005 Internet System Consortium
All Rights Reserved
For Info please visit http://www.isc.org/products/dhcp
Listen to LPF/eth0/00:eo:4d:15:43:13
Sending on LPF/eth0/00:eo:4d:15:43:13
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
NO DHCPOFFERS RECIVED
no working leases in persistent database
sleeping

```

---

### Post by mooscape on 2006-10-29
2pacapalypse

I have pretty much the same problem.  It appears we should be getting a response on IP-v4 giving the IP address, netmask and broadcast address.

This is what a working connection (same cable plugged into my hp rather than my IBM) should look like:
mooscape@mooscape-laptop:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:02:3F:21:A8:A4
          [COLOR="Red"]inet addr:222.125.41.118  Bcast:222.125.63.255 Mask:255.255.224.0[/COLOR]
          inet6 addr: fe80::202:3fff:fe21:a8a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:77494 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2696 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6585742 (6.2 MiB)  TX bytes:430962 (420.8 KiB)
          Interrupt:201 Base address:0x8800




However, like you I am getting :


mel@mel-laptop:~$ sudo ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:06:1B: D0:0D:6C
          inet6 addr: fe80::206:1bff:fed0:d6c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21367 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1345052 (1.2 MiB)  TX bytes:7434 (7.2 KiB)

mel@mel-laptop:~$ sudo ifup eth0
ifup: interface eth0 already configured
mel@mel-laptop:~$ sudo ifdown eth0 && sleep 10 && sudo ifup eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:06:1b:d0:0d:6c
Sending on   LPF/eth0/00:06:1b:d0:0d:6c
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:06:1b:d0:0d:6c
Sending on   LPF/eth0/00:06:1b:d0:0d:6c
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.  ](*,) 

No end in site....

---


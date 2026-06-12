---
title: "Wi-Fi won't start"
date: 2005-09-18
forum: Desktop Environments
---

### Post by MadPriest on 2005-09-18
After posting [here](http://www.ubuntuforums.org/showthread.php?t=66095) that everything works fine with clean Breezy install, this morning i updated the system.
Since the update, my wireless doesn't seem to start.  
I have IBM t40 laptop with Cisco AiroNet 802.11b card.
Since it didn't want to start, i tried to change settings in /etc/network/interfaces.
Now it looks like this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth0

# The primary network interface
auto eth0
iface eth0 inet dhcp
        # wireless-* options are implemented by the wireless-tools package
#       wireless-mode managed
#       wireless-essid any
#       wireless-key off
#       up iwconfig eth0
``` 
When i try ifup eth0, i get :
```
run-parts: /etc/network/if-pre-up.d/whereami exited with return code 1
There is already a pid file /var/run/dhclient.eth0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
eth0: unknown hardware address type 801
sit0: unknown hardware address type 776
eth0: unknown hardware address type 801
Listening on LPF/eth0/
Sending on   LPF/eth0/
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

``` 
Anything i can do?

P.S.
I can get to "K-System Settings - Network Settings", but i can't get into "Administrator mode"

The ifconfig looks like:
```
ifconfig
eth0      Link encap:UNSPEC  HWaddr 00-0E-9B-48-A1-4E-B8-79-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:2312  Metric:1
          RX packets:600 errors:19 dropped:0 overruns:0 frame:19
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:115099 (112.4 KiB)  TX bytes:202 (202.0 b)
          Interrupt:11 Base address:0x8000

eth1      Link encap:Ethernet  HWaddr 00:0D:60:36:DF:DA
          inet addr:10.0.0.165  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:60ff:fe36:dfda/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7027 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8038443 (7.6 MiB)  TX bytes:673047 (657.2 KiB)

eth2      Link encap:Ethernet  HWaddr 00:0E:9B:48:A1:4E
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:600 errors:19 dropped:0 overruns:0 frame:19
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:115099 (112.4 KiB)  TX bytes:202 (202.0 b)
          Interrupt:11 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:417 errors:0 dropped:0 overruns:0 frame:0
          TX packets:417 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:43105 (42.0 KiB)  TX bytes:43105 (42.0 KiB)
``` 

The eth0 should be Cisco Wi-Fi.
eth1 - Intel onboard network card.

I have no idea what is eth2.

---

### Post by mlomker on 2005-09-18
> run-parts: /etc/network/if-pre-up.d/whereami exited with return code 1


You should disable whereami until you figure out your other problems.  It can really make things confusing, depending upon what rules you have configured.  Temporarily renaming your whereami.conf file should suffice.

> 
I can get to "K-System Settings - Network Settings", but i can't get into "Administrator mode"


Running breezy, I suppose?  The control applets are still a mess.

> 
I have no idea what is eth2.

It has the same hardware address as eth0.  Do yourself a favor and take a look at /etc/iftab.  This file allows you to match a hardware address to a device name.  I renamed my 'eth1' to 'wlan0', for example.  If you don't put the devices in there then the names can change periodically with kernel updates.

As far as your problem is concerned, I'm not sure.  Start by looking through the contents of **dmesg | more** and **lsmod | more**.  You need to figure out the name of the driver that is loading for the card and look for error messages that relate to it in the dmesg (kernel) log.

---

### Post by MadPriest on 2005-09-19
**mlomker**, thanks for reply.
First, i removed the whereami.
Second, i changed **/etc/iftab**:
```
wlan0 mac 00:0e:9b:48:a1:4e
``` 
Third, according to **dmesg | more** , there's no problem loading driver of the Cisco Wi-Fi, and i see it in **lsmod | more** : ```
airo      63776  0
``` 
Now, when i run **/etc/init.d/networking restart** , i get 
```
There is already a pid file /var/run/dhclient.wlan0.pid with pid 6682
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
wlan0: unknown hardware address type 801
sit0: unknown hardware address type 776
wlan0: unknown hardware address type 801
Listening on LPF/wlan0/
Sending on   LPF/wlan0/
Sending on   Socket/fallback
ifup: interface lo already configured
There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
wlan0: unknown hardware address type 801
sit0: unknown hardware address type 776
wlan0: unknown hardware address type 801
Listening on LPF/wlan0/
Sending on   LPF/wlan0/
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

And, again, i see wlan0 at ifconfig:
```
 ifconfig
eth1      Link encap:Ethernet  HWaddr 00:0D:60:36:DF:DA  
          inet addr:10.0.0.165  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:60ff:fe36:dfda/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2267 errors:0 dropped:0 overruns:0 frame:0
          TX packets:437 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:195815 (191.2 KiB)  TX bytes:65097 (63.5 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1322 (1.2 KiB)  TX bytes:1322 (1.2 KiB)

wlan0     Link encap:UNSPEC  HWaddr 00-0E-9B-48-A1-4E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:2312  Metric:1
          RX packets:2182 errors:62406 dropped:0 overruns:0 frame:62406
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:269759 (263.4 KiB)  TX bytes:202 (202.0 b)
          Interrupt:11 Base address:0x8000 

wlan2     Link encap:Ethernet  HWaddr 00:0E:9B:48:A1:4E  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2182 errors:62406 dropped:0 overruns:0 frame:62406
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:269759 (263.4 KiB)  TX bytes:202 (202.0 b)
          Interrupt:11 Base address:0x8000 
```

---

### Post by mlomker on 2005-09-19
> 
wlan0     Link encap:UNSPEC  HWaddr 00-0E-9B-48-A1-4E-00-00-00-00-00-00-00-00-00-00  


The 'unspecified' link encapsulation and the invalid MAC address are something that I've never seen before.  

The dual ethernet interfaces for one card may be unique to the Cisco card, but I'm afraid that the problem is too specific for me to have any suggestions.

---

### Post by MadPriest on 2005-09-20
Thanks for reply and trying to help.
I rolled back to Hoary.
At least i have no problem with wireless.
The strangiest thing is that the /etc/network/interfaces file is the same

---

### Post by FLeiXiuS on 2005-09-20
Typically this happens when the card is confused about the MODE it's in.  You could very well easily, remove the card and re-insert it for hotplug to reconfigure the modules.

Can you do it manually?  Remove the card at boot so hotplug doesn't pick it up.  Re-insert and `modprobe cisco`.  

And by the way, cisco cards you eth* rather then wlan*.  This would approach your problem with the UNSPEC.  Since you changed the iftab.  That'd be a huge problem, now you have the drivers confused...

Again approach manually, then bring the interface up.  Make sure your network card has the appropriate lights.  If so, check out iwconfig.  See what's happening!

---

### Post by MadPriest on 2005-09-21
Well, i think removing MiniPCI card on boot from laptop isn't so easy   [-X 
But it's my mistake I didn't write it down

---

### Post by FLeiXiuS on 2005-09-21
Ooh, well..just restart hotplug, that'll do it.

---

### Post by MadPriest on 2005-09-23
Restarting hotplug didn't help.
Anyway, i'm with Hoary now. 
But i will upgrade to Breezy as soon as it will be released officially

---

### Post by MadPriest on 2005-09-23
By the way, seems like the problem is with the kernel 2.6.12, cause i just upgraded again but switched to kenel 2.6.10 - everything works fine

---

### Post by sterni1971 on 2005-10-11
I have exactly the same result it don't seems to be solved. I don't
think that this is related to kernel. My dist-upgrade was interrupted
before the new kernel was installed. I finished the installtion with
wire, but even with an complete breezy I couldn't set up
wi-fi with aironet card. the output looks exactly like described,
an restart of the hotplug system shows no results. i could
even see the SSID of my AP, but i get no dhcp.

regards

---

### Post by byronclark on 2005-10-14
[QUOTE=MadPriest]**mlomker**, thanks for reply.
First, i removed the whereami.
Second, i changed **/etc/iftab**:
```
wlan0 mac 00:0e:9b:48:a1:4e
``` 
[/QUOTE]

The airo driver creates two interfaces: one for normal use and one for monitor mode.  The best fix is to change [FONT="Courier New"]/etc/iftab[/FONT] to look like this:
```
wlan0 mac 00:0e:9b:48:a1:4e arp 1
```

---

### Post by Teleyinex on 2005-10-15
im here with the same problem. I dont know why always ifconfig gets first the unspec card instead of the second one.

---

### Post by mbr on 2005-10-15
HELP! Exactly the same here on (K)ubuntu 5.10. I can't use my e100, nor the airo / cisco network card. It is so stupid, having NO networking available! PLEASE PLEASE Ubuntu/Kubuntu guys, any idea ? If you need any further technical descriptions, please let us all know! Thanks Bye, Markus who's switching back to Hoary :-(

---

### Post by Teleyinex on 2005-10-15
Well, I have a little "crap" fix, but works for me. If you have at least that your ubuntu sets your card as *wlan0 with link encap: UNSPEC*, and *wlan1 is the one with link encap: Ethernet*, you are ok with this script. The script is the next one:

In my case I want to have an ad-hoc network, with the **ssid: chachi** and **ip 192.168.0.1**, because the wlan1 its the good one adaptor and the gateway for this wifi home-network. This is the code:

#/bin/bash
iwconfig wlan1 mode ad-hoc essid chachi
ifconfig wlan1 192.168.0.1 up
/etc/init.d/dhcp3-server restart

Well, the dhcp3-server is only needed if you want to give ips for your network, in my case this is necessary so I restart it. If this isnt your case, comment it out, or delete it.

This code is in /etc/init.d/wifi and in /etc/rc2.d/S91wifi. With this is solved. If you have any question I will try to answer it.

Another thing, if you want to have another ssid you only have to change it, the same for the mode of the card.

Sorry about my english. ;)

---

### Post by mbr on 2005-10-15
[QUOTE=Teleyinex]
#/bin/bash
iwconfig wlan1 mode ad-hoc essid chachi
[/QUOTE]
Hmmm, it doesn't work with my cards (airo/cisco & e100), as my wireless card doesn't response at all to any configurations. I can do an iwconfig, and it shows my interfaces, but essid is not changing even if I try to do so (like in your command above!).

What about others ?

---

### Post by sterni1971 on 2005-10-17
[QUOTE=byronclark]The airo driver creates two interfaces: one for normal use and one for monitor mode.  The best fix is to change [FONT="Courier New"]/etc/iftab[/FONT] to look like this:
```
wlan0 mac 00:0e:9b:48:a1:4e mac 1
```[/QUOTE]

yes exactly. first i just made an ifconfig eth2 up and a dhclient3 eth2 to
get my inet (to read the posting again ;-) and after changing the
line everything is fine. there is only one question why does happen
in the world best distro :???: 

so thanks again

sven

---

### Post by aivars on 2005-10-19
Hello,
I have exactly the same problems as MadPriest with Asus WL-138g PCI wireless card. Having already lost 2 whole evenings on trying to bring up wireless card (i use ndiswrapper) i am starting to give up. I will try the previous release of Ubuntu (now 5.10) as i understand it maight help or switch to other Linux package.
I am very dissapointed actually - wireless in Windows xp is a breeze.


Thanks

Aivars

---

### Post by skirov on 2005-10-21
I have similar problem- just upgraded to 5.10 and my dhcp client cannot  get a dynamic IP anymore. A laptop I have with hoary works fine. I am not good enough (and patient :cool: ) to work the problem out, so I just got myself a static IP address for this machine. Forget he dynamic IP. Not elegant approach, but works for me.

---

### Post by crainte on 2005-10-24
Has anyone fixed the problem yet? or are we limited to hoary/breezy with the 2.6.10 kernel?

---

### Post by mbr on 2005-11-21
[QUOTE=crainte]Has anyone fixed the problem yet? or are we limited to hoary/breezy with the 2.6.10 kernel?[/QUOTE]
No - I haven't fixed the problem yet.

Any ideas guys ??? I am still stuck with Hoary :-( 
Also see: [http://bugzilla.ubuntu.com/show_bug.cgi?id=17894]("http://bugzilla.ubuntu.com/show_bug.cgi?id=17894")

---


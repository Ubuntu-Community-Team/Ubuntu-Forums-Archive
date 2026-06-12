---
title: "Network Manager Issues"
date: 2006-06-02
forum: Desktop Environments
---

### Post by Leebobs on 2006-06-02
I have installed network manager through the Add/Remove applications option. Problem being it doesn't detect any wireless networks.

I have a Dell Inspiron 6000 laptop, with the standard intel wireless card installed.

Do I need to start a service or anything? 

Thanks

Leebobs

---

### Post by PriceChild on 2006-06-02
Same here :(

---

### Post by Melvil on 2006-06-02
Please open a terminal and type "iwconfig". Post your output here.

---

### Post by Leebobs on 2006-06-02
[QUOTE=Melvil]Please open a terminal and type "iwconfig". Post your output here.[/QUOTE]

andy@andy-laptop:~$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"3Reeves"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:B5:C6:55:38
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=73/100  Signal level=-55 dBm  Noise level=-80 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

-------------------
Hope this helps

Leebobs

---

### Post by PriceChild on 2006-06-02
```
pricechild@thebeast:~$ iwconfig
lo        no wireless extensions.

ra0       RT2500 Wireless  ESSID:""
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-192 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

eth1      no wireless extensions.

vmnet8    no wireless extensions.

vmnet1    no wireless extensions.

sit0      no wireless extensions.

ppp0      no wireless extensions.

```

---

### Post by Melvil on 2006-06-02
Okay this is easily fixed.

Type this into terminal:
```
gksu gedit /etc/network/interfaces
```

This will open a text editor. Now look for these lines:

for Leebobs
```
auto eth1
iface eth1 inet dhcp
```

for PrinceChild:
```
auto ra0
iface ra0 inet dhcp
```

Make sure that there are no other lines belonging to this interface, i.e. if there are some lines like "wireless_yes", "wireless_mode", "wireless_*",
uncomment them by putting a dash "#" in front of those lines.

You will end up with a file like this

```

... some configuration for other interfaces ...

auto eth1/ra0
iface eth1/ra0 inet dhcp
# you may also remove these lines if you don't need a fixed configuration and let NM do all the job
#wireless yes
#wireless_mode managed
#wireless_....

... some configuration for other interfaces ...
```

Next:

restart your network:
```
sudo /etc/init.d/networking restart
```

reload NetworkManager:
```
sudo /etc/init.d/dbus restart
```

The reason behind this is, that NetworkManager only handles interfaces that are entirely unconfigured. If you have a fixed ESSID or IP set, then NM won't touch these interfaces

Hope this helps :)

---

### Post by tgstarfire on 2006-06-02
Okay I tried all of this above, and now I still am in the same boat.  my network manager shows this

-------------------------
wired (greyed out when unplugged)
wireless networks
--------------------------
connect to other wireless network
create new wireless network
-------------------------

even when i try to create the network manually, it doesnt give me anything.  The wireless connected light on my notebook is on, so I know its doing something (i got it to at least light up last nite)  i switched from mandriva, which somehow got the wireless to work, so I know it can be done, im just at my wits end here.  anyone give me a hand?

tgstarfire@tgstarfire-laptop:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=15 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

---

### Post by Leebobs on 2006-06-02
Melvil you star!! Now works perfectly.

Many thanks

Leebobs

---

### Post by PriceChild on 2006-06-02
THe lines you suggested i add were already there :)

Just restarted networking and all is good! :)

Thanks, Pricey

---

### Post by Melvil on 2006-06-02
[QUOTE=tgstarfire]Okay I tried all of this above, and now I still am in the same boat.  my network manager shows this

-------------------------
wired (greyed out when unplugged)
wireless networks
--------------------------
connect to other wireless network
create new wireless network
-------------------------
[/QUOTE]

I have no experience with broadcom chips, but I'm a bit confused about the "Access Point: Invalid" line. For me it shows "Access Point: Not-Associated" when not connected. But since NM offers you to create a network it at least seems to have found your wireless card.
There has been a lot of discussion about broadcom chips during the development of Dapper, have you tried using the search feature?

If you don't find help in any of the older threads you might want to do this:

```
sudo killall NetworkManager NetworkManagerDispatcher
sudo NetworkManager --no-daemon
```

This will generate debug output. You might want to compare it against other people's output offered in some of the older threads.

---

### Post by Kropotkin on 2006-06-02
Hi Melvil,

Thanks, this information is really helpful. I now have NetworkManager working fine here.

One question: I'd like to set things up so that

1.) when at home, I connect to my wap with a fixed IP and 64-bit WEP key;

2.) when elsewhere, I connect to whatever wap is around, without having a long timeout at boot time while the system waits for the network to come up.

Suggestions how to go about this?

TIA

---

### Post by Melvil on 2006-06-02
I still haven't found a clean solution for this (btw. you can speed up the boot process by hitting Ctrl+C to skip the network configuration)
But I imagine it should be perfectly possible to write a script that comments/uncomments the lines to switch between configured/unconfigured network interfaces and then restarts the network.
There's also a "location" profile in the gnome network settings, but I haven't tried it yet.

---

### Post by russianbandit on 2006-06-02
That's a buch Melvil. This has been bothering me for a while. Good explanation.

---

### Post by swamytk on 2006-06-03
[QUOTE=Melvil]

The reason behind this is, that NetworkManager only handles interfaces that are entirely unconfigured. If you have a fixed ESSID or IP set, then NM won't touch these interfaces

Hope this helps :)[/QUOTE]

Thank you so much! I too had that problem. Solution is readily available by you at Forums! Great Community effort!

---

### Post by howardf42 on 2006-07-22
I have followed this thread and the suggestions made by Melvil, but without the same results.  Here's what I've got.  A Dell Inspiron 6000 with Ehternet and Wireless connections.  Neither connection loads at boot, but the following command gets the Wireless started, but not the Ethernet connection.

```
sudo ifdown eth0 && sudo ifup eth0 && sudo dhclient eth0
```

and

```
sudo ifdown eth1 && sudo ifup eth1 && sudo dhclient eth1
```

Here's what my /etc/network/interfaces file looks like:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid *******
wireless-key **********

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface dsl-provider inet ppp
provider dsl-provider

```

I then run 

```
sudo /etc/init.d/networking restart
```

with the following results:

```
 * Reconfiguring network interfaces... postconf: fatal: open /etc/postfix/main.cf: No such file or directory
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:13:ce:21:be:3e
Sending on   LPF/eth1/00:13:ce:21:be:3e
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 172.16.0.1 port 67
Continuing at if-pre-up,wired,lan
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:12:3f:e1:1a:df
Sending on   LPF/eth0/00:12:3f:e1:1a:df
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 172.16.0.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 172.16.0.1
Failed to bring up eth0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:13:ce:21:be:3e
Sending on   LPF/eth1/00:13:ce:21:be:3e
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 172.16.0.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 172.16.0.1
bound to 172.16.1.37 -- renewal in 1724 seconds.
Moving from if-pre-up,wired,lan to dhclient3,wired,lan
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
Moving from dhclient3,wired,lan to if-pre-up,wired,lan
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Continuing at if-pre-up,wired,lan
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Continuing at if-pre-up,wired,lan
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

```

I see two separate but related issues here.  Wireless will restart but not automaticly at boot.  Ethernet won't start at all.

Thanks in advance for your help.

Saludos,
Howard

---

### Post by siucdude on 2006-07-22
> **Melvil said:**
> Please open a terminal and type "iwconfig". Post your output here.

I tried the same almost and I don't get an IP address but it finds the access point.  look below.

siucdude@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     Auto  ESSID:"tjoniak2"  Nickname:"tjoniak2"
          Mode:Auto  Channel:0  Access Point: 00:18:3F:0C:03:61   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:100/100  Signal level:-58 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
any help would be great.

Thanks

---


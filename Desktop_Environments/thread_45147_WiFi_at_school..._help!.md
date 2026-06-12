---
title: "WiFi at school... help!"
date: 2005-06-28
forum: Desktop Environments
---

### Post by stray on 2005-06-28
I'm a grad student at Pratt Institute and I'm having trouble getting on the school's wireless network. According to their "how to connect to the wireless network" paper (which is purely Windows/Mac, btw), it's basically set the SSID, use DHCP and one nasty catch.

Apparently, when you connect with your Windows/Mac machine, you're supposed to get a popup in your web browser asking for the login and password you use on the school's mail system. However, I don't get it. I just get a great big nothing from the system and "suchandsuch.com could not be found" in Firefox.

Does anyone else have to jump through this particular hoop? Is there some weird trick to this I'm not aware of? Is there a way to specify login/pass in the connection config?

---

### Post by circussideshow on 2005-06-29
i'm fairly new to all this as well, but i've been able to use iwlist eth1 scanning  to see my available APs and then manually setup iwconfig with the desired AP info.  sometimes i'm able to get some dhcp action for an IP, and then i have been able to point my browser to the default gateway.  someone else recommended to me that if the usual .1 gateway doesn't work to try .1-.10 and .245-.254 due to possible networking architecture and layout.  i've seen some decent posts on this here at ubuntu forums, so i recommend you do a little searchin as well. :grin:

---

### Post by stray on 2005-06-29
I can't seem to use iwlist. When I run **iwlist eth1 scanning**, I get:
*eth1      Interface doesn't support scanning : Operation not supported*
I tried it through sudo and got the same thing.

---

### Post by jarno on 2005-06-29
[QUOTE=stray][I]eth1      
Interface doesn't support scanning : Operation not supported[/I][/QUOTE]

Is eth1 your wlan-card, or is it ethernet interface?
In my laptop wlan-card is ra0 (ralink chipset) and in my desktop machine wlan-card is ath0 (atheros chipset).

--
    /jarno

---

### Post by stray on 2005-06-29
eth1 is the wifi interface.

---

### Post by tomchuk on 2005-06-29
[QUOTE=stray]I'm a grad student at Pratt Institute and I'm having trouble getting on the school's wireless network. According to their "how to connect to the wireless network" paper (which is purely Windows/Mac, btw), it's basically set the SSID, use DHCP and one nasty catch.

Apparently, when you connect with your Windows/Mac machine, you're supposed to get a popup in your web browser asking for the login and password you use on the school's mail system. However, I don't get it. I just get a great big nothing from the system and "suchandsuch.com could not be found" in Firefox.

Does anyone else have to jump through this particular hoop? Is there some weird trick to this I'm not aware of? Is there a way to specify login/pass in the connection config?[/QUOTE]

They're probably using something like [Nomadix](http://www.nomadix.com/) which is basically a proxy and some dns trickery to make you login before you can access the network.

First thing's first though:
when you run:```
iwconfig eth1 essid <school's ssid>
```, then run iwconfig eth1, does is show that you are connected to an AP? Does it list a MAC address, channel, etc for the AP? It should look something like:
```

eth1      IEEE 802.11-DS  ESSID:"pratt"
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:00:33:44:55:66
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535
          Retry limit:16   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=121/160  Signal level=-27 dBm  Noise level=-97 dBm
          Rx invalid nwid:1264586  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4106279   Missed beacon:0

```

If that's fine, you have to make sure you're getting an IP. If the network is DHCP as you say, you should have the line:
```
iface eth1 inet dhcp
```
somewhere in /etc/network/interfaces. Do you? If not, add it. Once that is set up and iwconfig is showing that you are connected to an AP, you should be able to type "ifup eth1" and it will get an IP through DHCP. Check that this as happened by issuing the command "ifconfig eth1" and check that the interface is indeed up and you have an IP, should look like:
```

eth1      Link encap:Ethernet  HWaddr 00:11:22:33:44:55
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:8aff:feea:59f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:1127984 dropped:0 overruns:0 frame:1127984
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1168 (1.1 KiB)  TX bytes:862 (862.0 b)
          Interrupt:9 Base address:0x8000

```

Once this is all done, you should be able to point your browser to any site and the software should redirect you to the login page. You may need to whitelist the page to allow popups in Firefox, or disable popup blocking altogether until you figure everything out.

Try all that and let us know if you make any progress.


EDIT: Also if you're having trouble with iwlist you may have to bring up the interface first:
```
ifconfig eth1 up
```

---

### Post by stray on 2005-06-30
Ok. So can you tell me how this is any different from using the network-admin applet?

---

### Post by tomchuk on 2005-06-30
[QUOTE=stray]Ok. So can you tell me how this is any different from using the network-admin applet?[/QUOTE]
 Nope, I don't use Gnome :) When in doubt, do it the old fashioned way.

If you're going to use the applet, and this information is available through it, make sure you're associated to a real AP, make sure your getting an IP, and it should work.

---

### Post by stray on 2005-06-30
tomchuk: Everything in your tutorial checked out A-OK...until, that is, it tried to bring the interface up.

Here's the result of the first parts:
```
robert@tomservo:~$ sudo iwconfig eth1 essid "Pratt Institute"
robert@tomservo:~$ iwconfig eth1
eth1      IEEE 802.11-DS  ESSID:"Pratt Institute"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:4C:F1:BF
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   Sensitivity:1/3
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off

robert@tomservo:~$
```

Here's the applicable part of my /etc/network/interfaces:
```
# The primary network interface
iface eth1 inet dhcp
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid any
	wireless-key1 xxxxxxxxxx
auto eth1
```

Now, my home network requires a WEP key, but the school doesn't. however, I really don't want to replace that file every time. On the other hand, as you'll see next, I don't think it's the cause.

Here's what I got in the console when I tried to bring up the wireless interface:
```
robert@tomservo:~$ sudo ifup eth1
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:02:2d:5d:cf:c1
Sending on   LPF/eth1/00:02:2d:5d:cf:c1
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
robert@tomservo:~$
```
Everything was just fine until I tried to bring it up! What did I do wrong?

---

### Post by tomchuk on 2005-06-30
When you bring up the interface with ifup, it applies the WEP key and enables WEP, and of course this doesn't work with the Pratt AP. You can get rid of the wireless bits in your interfaces file, and it should work fine at shcool. Use waproamd to manage your wep key for home. You can have waproamd apply a wep key for any given SSID or AP MAC address, so it will still be automatic when at home, and will work at school.

I use a different system - I've left out any wireless bits in the interfaces file, and have written scripts for home and school (I go to Pace in NYC).

I've got a couple scripts in /usr/local/bin called whome (wirelss, home) and wpace (wireless, pace) which look something like:

```

#!/bin/sh
## whome - Bring up wireless interface at home
ifdown -a
iwconfig eth1 essid <essid> key <wep_key>
ifup eth1

```
```

#!/bin/sh
## wpace - Bring up wireless interface at school
ifdown -a
iwconfig eth1 essid <essid>
ifup eth1

```

---

### Post by stray on 2005-08-02
At last, at long last, I figured this out. It really was just a matter of using *iwconfig* to set the ESSID and to *turn the freaking encryption off*. Doh!

Thanks for the help, tomchuk.

---


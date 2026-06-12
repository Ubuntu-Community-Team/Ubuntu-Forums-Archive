---
title: "Dell Mini 9 wifi trouble"
date: 2009-01-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sanubie on 2009-01-01
My Dell mini doesn't want to allow me wifi access. The strange thing is I can get in my car and drive around detecting all the hotspots. It picks up on the signals. When I go to connect it says it is connected to whatever wifi network, but my browser still won't access the internet. Can anyone help me? 

I'm looking at it right now, and it shows 2 bars under connection. Shouldn't it work?

---

### Post by sirebral on 2009-01-01
Did you read the thread entitled, "If you need help with your DELL Mini, read this." ?  It's just a few posts down.

---

### Post by sanubie on 2009-01-02
> **sirebral said:**
> Did you read the thread entitled, "If you need help with your DELL Mini, read this." ?  It's just a few posts down.

Yea, but I didn't see anything similar to what I was experiencing. Like I said, it basically connects. It picks up on wifi signals. But for some reason I still cannot access the net. My browser won't pick up on it. My connections display says I'm connected at 40%. Maybe the firewall is blocking me. But the connection itself is not protected.

---

### Post by armandh on 2009-01-02
is this the first use or was it working and quit?
I would try and re establish your connection.
system>preferences>network configuration>wireless tab
select your wireless then edit
check your IPv4 settings I suggest automatic DHCP
[not local only]
also be sure airplane mode is not on.

I am running 8.10 so YMMV but as I recall it is the similar on the wife's laptop running 8.04

---

### Post by liviubero on 2009-01-02
Hi,
I am having a problem with wifi.
I just installed Intrepid on my Mini 9 and wanted to connect with my home wireless network. But Network Manager just keeps asking me for the password... Yes, I have the right password, it is writen on the modem itself.
The network is wep-protected.

Here some other infos:
```
sudo iwlist eth1 auth
eth1      Authentication capabilities :
        WPA
        WPA2
        CIPHER-TKIP
        CIPHER-CCMP
          Current WPA version :
          Current Key management :
        802.1x
          Current Pairwise cipher :
        none
          Current Pairwise cipher :
        none
          Current TKIP countermeasures : no
          Current Drop unencrypted : yes
          Current Authentication algorithm :
        open
          Current Receive unencrypted EAPOL : no
          Current Roaming control : no
          Current Privacy invoked : no
```The card doesn't seem to be wep capable.

```
sudo lshw -C network
  *-network              
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:23:08:29:4e:13
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg

```The card seems to use the wl driver and not the Broadcome one.
I activated the firmware driver from System->Administration->Hardware Drivers but I get the same output.

Also, if I try to remove the wl module and load the b43, I loose my eth1 interface:
sudo rmmod wl
sudo modprobe b43

I can see my network in Network Manager and with sudo iwlist eth1 scan, but I cannot connect to it.
I haven't tried to connect to a wpa network or to a unencrypted one and I haven't tried any other method to connect.

Any ideas how to get this done (get connected) and how to use the Broadcome driver?

Thank you.

---

### Post by anjilslaire on 2009-01-02
the card is wep capable. However, i see references to WPA in your output above. I had trouble getting WPA to work on mine. I finally got it sorted here:
[http://ubuntuforums.org/showthread.php?t=1019121&page=2]("http://ubuntuforums.org/showthread.php?t=1019121&page=2")

Be sure to delete any connections you have in connection manager and start with new entries.

---

### Post by liviubero on 2009-01-02
Do you have the same output from sudo iwlist eth1 auth and lshw -C network?
Are you using the Broadcome driver? And if yes, how did you activated it?

---

### Post by lswest on 2009-01-02
> **liviubero said:**
> Do you have the same output from sudo iwlist eth1 auth and lshw -C network?
Are you using the Broadcome driver? And if yes, how did you activated it?

the wl IS the broadcom driver.  b43 is an unofficial driver that rips the firmware from windows drivers, the wl drivers are, to the best of my knowledge, native linux drivers.

Have you successfully connected to the network once before?
In any case, try this (I had a similar issue with WPA):
hit alt + F2 and type in "gconf-editor" (without the quotes)
there navigate to system-->networking-->connections-->1-->802-11-wireless-auth
there, remove any reference from group, proto and pairwise for anything but WEP.  If you have more than just "1" in the connections list, check the folder "connection" under each (so 1-->connection) and check the network name.
As I said, this was done with a WPA network, so it may be differently set up for your WEP network.

Oh, also, make sure that you're choosing the right encryption type when giving in the passphrase (WEP 40/128 passphrase if it's a passphrase, or else a WEP 40/128 Key if it's the actual HEX value) - it should be in a drop-down menu above the text box for the passphrase.

---

### Post by anjilslaire on 2009-01-02
indeed:
```

eth1      Authentication capabilities :
		WPA
		WPA2
		CIPHER-TKIP
		CIPHER-CCMP
          Current WPA version :
		WPA2
          Current Key management :
		PSK
          Current Pairwise cipher :
		none
          Current Pairwise cipher :
		none
          Current TKIP countermeasures : no
          Current Drop unencrypted : yes
          Current Authentication algorithm :
		open
          Current Receive unencrypted EAPOL : no
          Current Roaming control : no
          Current Privacy invoked : no

```
and
```

laire@nightcrawler:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:21:63:ae:5b:05
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=192.168.1.100 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:d8:2f:9a
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 6a:3c:4f:b9:32:e4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by lswest on 2009-01-02
Note, checking up on it, the WL drivers don't seem to offer support for WEP for broadcom 4312 chipsets.  Is there any chance you can change to WPA encryption?  It's much more secure anyways.

Seems like it at least: [http://bbs.archlinux.org/viewtopic.php?id=61580](http://bbs.archlinux.org/viewtopic.php?id=61580)

---

### Post by liviubero on 2009-01-02
> **lswest said:**
> Note, checking up on it, the WL drivers don't seem to offer support for WEP for broadcom 4312 chipsets.  Is there any chance you can change to WPA encryption?  It's much more secure anyways.

I cannot change it. It is a Sphairon Turbolink IAD W-Lan which used to be a router but my isp (Alice, Germany) cut off any router functions and made up a modem out of it. It just has a wep key on the back of it. That's all.
Thanks for the info. Now I know that it will never work.
Should I try with ndiswraper?

---

### Post by armandh on 2009-01-02
I think it would be easier to get a wireless hub that has the later encryption

---

### Post by BoundaryValueProblems on 2009-01-03
Hi.  I encountered a very strange problem.  I'm using ubuntu 8.04.1 preinstalled by Dell on my mini 9.  My wifi was working until this afternoon without too much trouble.  All of sudden, after I was away for a couple of hours, I got the similar wifi problem discussed in this forum.
It keeps me asking the WEP key... I entered the correct one, but it didn't connect anymore.  What's wrong with this?
The only thing I changed this afternoon after I came back to my mini 9 is the root password, but that shouldn't interfere this problem, I guess, right?
I would greatly appreciate if you could give me any help/pointer.

Thanks a lot!
BVP

---

### Post by lswest on 2009-01-03
> **liviubero said:**
> I cannot change it. It is a Sphairon Turbolink IAD W-Lan which used to be a router but my isp (Alice, Germany) cut off any router functions and made up a modem out of it. It just has a wep key on the back of it. That's all.
Thanks for the info. Now I know that it will never work.
Should I try with ndiswraper?

You can try ndiswrapper with the bcmwl5 windows driver, but I don't know if it will offer WEP encryption for your card.

To change settings on it you should be able to connect to it using an ethernet cable and going to the IP address that should be the router's config page (you'd have to google what address that is by default), but I don't know if you can change the key.  Does Alice offer any kinds of upgrade or so?  I know T-Online will send you an updated router for a (in my eyes not small) charge.

---

### Post by armandh on 2009-01-03
> **BoundaryValueProblems said:**
> Hi.  I encountered a very strange problem.  I'm using ubuntu 8.04.1 preinstalled by Dell on my mini 9.  My wifi was working until this afternoon without too much trouble.  All of sudden, after I was away for a couple of hours, I got the similar wifi problem discussed in this forum.
It keeps me asking the WEP key... I entered the correct one, but it didn't connect anymore.  What's wrong with this?
The only thing I changed this afternoon after I came back to my mini 9 is the root password, but that shouldn't interfere this problem, I guess, right?
I would greatly appreciate if you could give me any help/pointer.

Thanks a lot!
BVP

glad to see the problem solved
bal deleted

---

### Post by liviubero on 2009-01-03
> **lswest said:**
> You can try ndiswrapper with the bcmwl5 windows driver, but I don't know if it will offer WEP encryption for your card.

To change settings on it you should be able to connect to it using an ethernet cable and going to the IP address that should be the router's config page (you'd have to google what address that is by default), but I don't know if you can change the key.  Does Alice offer any kinds of upgrade or so?  I know T-Online will send you an updated router for a (in my eyes not small) charge.

This thing was a router, until they cut off any router functions. Now it is just a modem and you can access its "interface" only wifi and if have a static ip address. Spent hours with it.
I just bought myself a normal router and now it's alright.

I wouln't buy a router from them. They sell only garbage.

---

### Post by BoundaryValueProblems on 2009-01-03
> **armandh said:**
> no I think wrong.....
each start up needs the wifi password and regular 8.04.1 and 8.10 asks for the key ring password. I forget what the dell remix did as I no longer use it, but the key ring password may now not be functioning and need to be reset.

Thanks, armandh, for your comments.
But, all of sudden, it started working again.  The only reason I can think of is the following.
Yesterday, my son's friend came to our house with her laptop while I was away.  She connected her laptop to our wireless router.   This reached the maximum number of connected computers at home (I'm using comcast).  While I was writing my posting, she was here and using her laptop.  After posting it and after she left, all of sudden, it accepted the WEP key and it connected to the internet.
Apparently, however, the change of the root password had nothing to do with the wireless problem I had.

I hoped that the comcast router could issue some more diagnostic messages rather than kicking me out from connections...

Best regards,
BVP

---


---
title: "I can't connect to my wifi"
date: 2013-08-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by fred_wright on 2013-08-30
I'm new to linux. I would love it but I can't get wireless internet. No matter what I've done i can't connect to my wireless and am stuck to my ethernet. its really sad. please help
:icon_frown:-fred

---

### Post by kurt18947 on 2013-08-31
Hi Fred
I wonder if you'd have a better response if you posted in the networking and wireless section.  Are you familiar with how to open a terminal?  If you could post the result of one terminal command it might be a good starting point.  From the command prompt type "lshw -c network".  It is recommend to do this from a sudo account.  The result should look something like this:
```
 *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:df3ff000-df3fffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:2
       logical name: wlan3
       serial: xx:xx:xx:xx:xx:xx
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu ip=192.168.1.5 multicast=yes wireless=IEEE 802.11bgn

```

---

### Post by varunendra on 2013-08-31
Welcome to the forums fred_wright !

Another command to give us an idea of your hardware and driver in use is -
```
lspci -nnk | grep -iA2 net
```
It also gives the exact chip ID which is sometimes required to determine which driver is suitable for your card.

For a detailed report about your wireless setup, you can use "wireless_script" (created by Wild Man, Krytarik). You can find it with instructions in the post linked to the "Wireless Script" link in my signature.

---

### Post by johnnyzee on 2013-09-06
I am working with a Dell D630 Latitude (Ubuntu 12.04) and have also had trouble with wireless connectivity. Ethernet is okay. Recently I removed the STA driver and installed the B43 driver and my wireless worked for a couple of days. Now it appears that I am connected but cannot access the internet. I just ran the wireless script and placed the text into Pastebin at 

[http://pastebin.ubuntu.com/6070747/](http://pastebin.ubuntu.com/6070747/)

I would really appreciate if somebody could have a look and tell me what the problem might be.

Regards

---

### Post by johnnyzee on 2013-09-06
SOLVED - changed router settings from WEP to WPA-PSK, AES

Thanks to post by Varunendra [http://ubuntuforums.org/showthread.php?t=2172619#post12779960](http://ubuntuforums.org/showthread.php?t=2172619#post12779960)

---

### Post by varunendra on 2013-09-06
> **johnnyzee said:**
> I am working with a Dell D630 Latitude (Ubuntu 12.04) and have also had trouble with wireless connectivity. Ethernet is okay. Recently I removed the STA driver and installed the B43 driver and my wireless worked for a couple of days. Now it appears that I am connected but cannot access the internet. I just ran the wireless script and placed the text into Pastebin at 

[http://pastebin.ubuntu.com/6070747/](http://pastebin.ubuntu.com/6070747/)

I would really appreciate if somebody could have a look and tell me what the problem might be.

Regards
In a quick glance (I'm too hungry to pay more attention ;)), two things look adjustable -
1) You are using WEP key. It is outdated, less secure (almost unsecure) and doesn't work well with Linux. So if you can, try changing it to WPA2 with AES encryption in the router.

2) (maybe you won't need this step if you implemented above) Try fixing the speed to a compatible higher value -
```
sudo iwconfig wlan0 rate 48M
```
Other compatible speeds (as per the output you posted) are 36M, 24M, 54M etc. which you can try.

If this doesn't help, I'd recommend to post a new thread of your own and post the details of the problem as well as any backgrounds. If you create one, feel free to post a link to it here so I can follow, or PM me (or chili555, if you wish) to take a look at it.

**EDIT:**
Hoorray !! Posted simultaneously it seems, nice to see problem solved! :D

---


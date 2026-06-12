---
title: "If you need help with your Mini 9 - READ THIS"
date: 2008-12-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by magicfab on 2008-12-30
Anyone owning a Mini 9 should take a good look at this wiki page:
[https://help.ubuntu.com/community/DellMini9](https://help.ubuntu.com/community/DellMini9)

It lists common issues for the Mini 9 with Ubuntu, either pre-installed from factory or installed from an Ubuntu vanilla 8.04.1 CD.

It also has direct links to the documentation that came with the computer in electronic form, as well as links to other community sites, forums and mailing lists.

If you have a specific question about the Mini 9, it is also possible to ask it here:
[https://answers.launchpad.net/dell-mini/+addquestion](https://answers.launchpad.net/dell-mini/+addquestion)

I can't answer all questions here in the forum, but I keep a close eye on questions asked via Launchpad.

Thank you.

---

### Post by armandh on 2008-12-31
thank you for past and future help to the mini 9 community.
I now have my mini 9 set up the way I want [dual XP/8.10 boot]
It has moved from the basement tech bench to the office desk. 
XP will be used to take QuickBooks to meetings. all else Ubuntu!

---

### Post by liviubero on 2009-01-01
Hi,
On the above mentioned sites I didn't find an answer to this question:
I just installed Intrepid on my Mini 9 and wanted to connect with my home wireless network. But Network Manager is just keeping asking me for the password...
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

I can see my network in Network Manager, but I cannot connect to it.
I haven't tried to connect to a wpa network or to a unencrypted one.

Any ideas how to get this done (get connected)?

Thank you.

---

### Post by magicfab on 2009-01-02
Please do not ask questions in this thread.

Instead register to Launchpad.net and ask them here:
[https://answers.launchpad.net/dell-mini/+addquestion](https://answers.launchpad.net/dell-mini/+addquestion)

Or open a new thread in this forum.

Thank you.

---


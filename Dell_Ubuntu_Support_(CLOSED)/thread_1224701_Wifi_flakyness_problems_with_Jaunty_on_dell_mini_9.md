---
title: "Wifi flakyness problems with Jaunty on dell mini 9"
date: 2009-07-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by arielgr on 2009-07-27
Hi,

So I bought a dell mini 9 several months ago and everything worked ok with the dell hardy stock distribution. Then I upgraded to jaunty (9.04) and after a couple of weeks I started getting problems with my wifi adapter. Basically the wifi will stop working after some time (between 2 mins and 1 hour or so) after reboot.

The Mini 9 has the broadcom 4312, using propiatry broadcom drivers (wl)
lspci
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

Once the flakyness starts, the wifi will just drop and nothing will go through.
When I try to run sudo iwlist scan (eth1 is the wireless adapter)
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
eth1      Failed to read scan data : Invalid argument

I also tried to remove and reinsert the module to the kernel, and interestingly this fails, the system logs contains the following error after a sudp modprobe -r wl, sudo modprobe wl
eth%d: 5.10.91.9 driver failed with code 11

I even reinstalled the whole OS and refused all updates as I though it was triggered by them, but it still hapened after a couple of days.

Does anyone else with Dell mini 9 and jaunty have issues with their wireless?
Is anyone's wifi working fine on Jaunty?

I am pretty sure this is a problem with the broadcom drivers, the only thing I think is to upgrade the kernel, apparently there were some patches by broadcom released for 2.6.29 or 30.. Does anyone know how to go on upgrading the kernel?

cheers,
Ariel

---

### Post by komputes on 2009-07-27
Hi Ariel,

In 8.04-lpia build there was a bug with the wireless. This is the workaround:

[https://help.ubuntu.com/community/DellMini9#Connecting%20to%20a%20wireless%20router](https://help.ubuntu.com/community/DellMini9#Connecting%20to%20a%20wireless%20router)

Personally, I took off the lpia build of ubuntu by installing the standard i386 version on top of it. If you use 9.04 I recommend you do the same.

---

### Post by jwaclawsky on 2009-07-27
I have a mini 9 running 9.04 for over a week with no problems. I have connected to 2 wireless LANS so far and no issues found. 

I'd go back to 8.04 and see if the you have the same problem.  Otherwise I suspect a configuration issue unless there is a difference between our mini 9's. I bought mine in April.

---

### Post by Offroadie on 2009-07-28
I have Jaunty running on two Mini 9s with no issues. They both connect fast and hold a connection.

---

### Post by ugm6hr on 2009-07-28
> **Offroadie said:**
> I have Jaunty running on two Mini 9s with no issues. They both connect fast and hold a connection.

9.04NBR (i386) runs fine on my Mini 9 too.  Wifi is very stable - better than the wired connection on my home server even!

---

### Post by arielgr on 2009-07-28
Hi guys,

thanks a lot for your help.

That is really weird. It seems the only difference is that I have installed the LPIA version rather than the 386 one, but I did have jaunty i386 installed previously and it didn't work either, after which I tried to reinstall..

Hmm.. Thats pretty weird as I have read many similar stories from other users. 

Could you please check which version of the broadcom wlan adapter you have using lspci (mine is rev 1).

cheers.

---

### Post by ugm6hr on 2009-07-29
> **arielgr said:**
> Could you please check which version of the broadcom wlan adapter you have using lspci (mine is rev 1).

lspci
```
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```

lshw
```
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:23:08:19:c5:33
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.1.2 latency=0 module=wl multicast=yes wireless=IEEE 802.11

```

Using default Network Manager 0.7 in Jaunty to connect.

Perhaps it is related to encryption (I use WPA), signal strength (my range is very good though), or your wifi router?  Seems unlikely that it would be a hardware issue...

---


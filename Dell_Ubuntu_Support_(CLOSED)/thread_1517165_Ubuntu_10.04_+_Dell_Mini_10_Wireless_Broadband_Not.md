---
title: "Ubuntu 10.04 + Dell Mini 10 Wireless Broadband Not Working"
date: 2010-06-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sam33 on 2010-06-24
Can anyone help, i have a dell mini 10 netbook with Ubuntu 10.04 but it  will not connect wirelessly to the internet anyone have any ideas !!!
I have a Netgear wireless ADSL2+ Modem Router.
All that happens is the little circle goes around then stops, no network connection.
I have cleared the password & reset but nothing.
I can connect wirelessly using a windows based laptop, but this netbook  will not connect any ideas would be appreciated.

I am a newbie to Ubuntu but have asked in other forums, and followed advice but no one seems to know how to fix the problem.
Please help .... In easy words.. Thanks

---

### Post by ajgreeny on 2010-06-24
This is probably down to the make of chipset in the wireless adapter in the computer and nothing to do with the router.  Do you know the adapter type in the machine?  If not, in a terminal run ```
sudo lshw -C network
```and report back the output here.

---

### Post by sam33 on 2010-06-25
> **ajgreeny said:**
> This is probably down to the make of chipset in the wireless adapter in the computer and nothing to do with the router.  Do you know the adapter type in the machine?  If not, in a terminal run ```
sudo lshw -C network
```and report back the output here.

Here is the results:- 

*-network               
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:25:56:6b:a6:ca
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:24:e8:bf:a3:c4
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:27 ioport:2000(size=256) memory:f0510000-f0510fff(prefetchable) memory:f0500000-f050ffff(prefetchable) memory:f0520000-f053ffff(prefetchable)

---

### Post by Denton Larson on 2010-06-25
Hi

Go to [http://www.ubuntumini.com/](http://www.ubuntumini.com/)

then scroll to Broadcom Wireless Driver Fix In Lucid

and try this

It worked for me I have a Dell Mini 10

Denton Larson

---

### Post by sam33 on 2010-06-25
> **Denton Larson said:**
> Hi

Go to [http://www.ubuntumini.com/](http://www.ubuntumini.com/)

then scroll to Broadcom Wireless Driver Fix In Lucid

and try this

It worked for me I have a Dell Mini 10

Denton Larson


It already said that this is installed and working properly.
So i'm afraid that did not work for me, any other ideas !!

---

### Post by sam33 on 2010-07-01
Anyone any ideas, still not resolved .........

---

### Post by mikewhatever on 2010-07-01
Try brining the interface up with the following command:
```
sudo ifconfig eth1 up
```

---

### Post by sam33 on 2010-07-02
> **mikewhatever said:**
> Try brining the interface up with the following command:
```
sudo ifconfig eth1 up
```

I have put that in and this is the message i got:-
"ethl: ERROR while getting interface flags: No such device

What does that mean ?

---

### Post by shiningkenmonster on 2010-07-04
you did not install the Broadcom wifi drivers correctly.

you have to actually install the Broadcom wifi drivers!

apparently you didn't install it.

follow the guide on ubuntumini.com

---

### Post by ugm6hr on 2010-07-04
I know this may seem like overkill, but it's important to give as much detail as possible.  See the Wifi help link below, and report back here.

Also - can you ensure you are copy / pasting commands & responses.

"ethl" and "eth1" are not the same - it's impossible to know whether you are typing commands or responses incorrectly unless you copy / paste here.

---

### Post by sam33 on 2010-07-05
> **shiningkenmonster said:**
> you did not install the Broadcom wifi drivers correctly.

you have to actually install the Broadcom wifi drivers!

apparently you didn't install it.

follow the guide on ubuntumini.com

How do you work that out then ?

If I go into System/Administration/Hardware Drivers it tells me that the Broadcom STA proprietary wireless driver is activated and currently in use !!!!!!!!!!

---

### Post by sam33 on 2010-07-05
> **ugm6hr said:**
> I know this may seem like overkill, but it's important to give as much detail as possible.  See the Wifi help link below, and report back here.

Also - can you ensure you are copy / pasting commands & responses.

"ethl" and "eth1" are not the same - it's impossible to know whether you are typing commands or responses incorrectly unless you copy / paste here.

Thanks for pointing out my typing mistake :roll:
It's a bit difficult to copy and paste when you are using two computers !!  ](*,)

---

### Post by mikewhatever on 2010-07-05
So, did it work when you typed eth1?  Did it work after a reboot, without using the command?

---

### Post by shiningkenmonster on 2010-07-05
> **sam33 said:**
> How do you work that out then ?

If I go into System/Administration/Hardware Drivers it tells me that the Broadcom STA proprietary wireless driver is activated and currently in use !!!!!!!!!!

When i was using the beta version of Karmic Ubuntu. I remember doing a fresh install. i remember it told me by default the Broadcom STA drivers are already installed. I knew this was an error, probably a bug. The Graphic User Interface was lying to me. because the wifi didn't work right out of the fresh install. i needed to download them. i deactivated the Broadcom STA and than restarted, hook up my Ethernet port unto my dell mini and and went to System -> Administration -> Hardware Drivers. clicked on installed the Broadcom STA drivers and restarted. the wifi works!

you never gave a clear answer, if you actually hooked up your Ethernet port onto your dell mini 10 and installed the Broadcom STA drivers. did you already do that? yes or no? or did you assume it was already installed?

---

### Post by shiningkenmonster on 2010-07-05
i was like to add:
i just noticed you have a Broadcom BCM4322 802.11a/b/g/n Wireless card.
back than dell used to offer the dell mini wireless-n cards for a short limited time.

back than people who was using this card on ubuntu reported that sometimes it wouldn't connect and sometime the speeds are very poor. and sometimes it works very well on other routers.

i personally had this problem too.

dell no longer offers this broadcom wireless wifi-N card for the dell mini 10 for Ubuntu anymore.

i had to personally call dell and told them the situation and they gave me the older broadcom wifi-g model card.

---

### Post by sam33 on 2010-07-08
> **ugm6hr said:**
> I know this may seem like overkill, but it's important to give as much detail as possible.  See the Wifi help link below, and report back here.

Also - can you ensure you are copy / pasting commands & responses.

"ethl" and "eth1" are not the same - it's impossible to know whether you are typing commands or responses incorrectly unless you copy / paste here.

Ok this time i put in, sudo iconfig ethl up
and the result for that was

sudo: iconfig:  command not found

---

### Post by ugm6hr on 2010-07-08
> **sam33 said:**
> sudo: iconfig:  command not found

Any chance you could try plugging into a wired ethernet cable?

You are still making typing errors.

If not, it is sensible to copy/paste using a USB stick to transfer between computers.

Anyway, I thought I should point out some links that might be worth reading...

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/560434](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/560434)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/564062](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/564062)
[http://ohioloco.ubuntuforums.org/showthread.php?p=9326032](http://ohioloco.ubuntuforums.org/showthread.php?p=9326032)

It looks like this might be a Network Manager bug with your card, but Wicd might solve.

---

### Post by sam33 on 2010-07-09
> **ugm6hr said:**
> Any chance you could try plugging into a wired ethernet cable?

You are still making typing errors.

If not, it is sensible to copy/paste using a USB stick to transfer between computers.

Anyway, I thought I should point out some links that might be worth reading...

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/560434](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/560434)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/564062](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/564062)
[http://ohioloco.ubuntuforums.org/showthread.php?p=9326032](http://ohioloco.ubuntuforums.org/showthread.php?p=9326032)

It looks like this might be a Network Manager bug with your card, but Wicd might solve.

Ok i typed it in correctly this time and the result is
ethl: ERROR while getting interface flags: No such device

So what does that mean?

---

### Post by sam33 on 2010-07-19
Is there anyone else that can help me before i throw the whole machine in the bin, it seems that ubuntu + Dell mini 10 + Wireless, Just do not work i have been trying to get an answer on these & other forums for a while now and no one seems to be able to help sort my problem, maybe there is no solution.....!

---

### Post by ugm6hr on 2010-07-20
I gave 3 links to various advice before.  Nevertheless, the STA driver should work:
[http://packages.ubuntu.com/lucid/bcmwl-kernel-source](http://packages.ubuntu.com/lucid/bcmwl-kernel-source)

Despite this, you have never managed to type a single command correctly. Without accurate details of the Terminal output, we cannot help. Full details from all questions in the Wifi help? link below would help get all details at one time.

I would strongly urge you to use an ethernet cable to connect to wired internet, else use a USB stick to copy/paste. By running all comands, this should not be too onerous.

Good luck, in any case.

---

### Post by sam33 on 2010-07-21
> **ugm6hr said:**
> I gave 3 links to various advice before.  Nevertheless, the STA driver should work:
[http://packages.ubuntu.com/lucid/bcmwl-kernel-source](http://packages.ubuntu.com/lucid/bcmwl-kernel-source)

Despite this, you have never managed to type a single command correctly. Without accurate details of the Terminal output, we cannot help. Full details from all questions in the Wifi help? link below would help get all details at one time.

I would strongly urge you to use an ethernet cable to connect to wired internet, else use a USB stick to copy/paste. By running all comands, this should not be too onerous.

Good luck, in any case.

I didn't realise i was here for spelling lessons, i thought this was supposed to be a helpful forum (?).
But my last post i typed correctly, and you have not told me what that meant (ethl: ERROR while getting interface flags: No such device)
all you did was comment on the typing again.

---

### Post by ugm6hr on 2010-07-21
> **sam33 said:**
> I didn't realise i was here for spelling lessons, i thought this was supposed to be a helpful forum (?).
But my last post i typed correctly, and you have not told me what that meant (ethl: ERROR while getting interface flags: No such device)
all you did was comment on the typing again.

It means you typed ethl, not eth1. i.e. a spelling mistake. This is not about giving you a spelling lesson, but trying to ensure you give us information with which we can help you.

It seems I am rubbing you the wrong way. Apologies for that.

---

### Post by Hairy_Hippo on 2010-08-02
> **Denton Larson said:**
> Hi

Go to [http://www.ubuntumini.com/](http://www.ubuntumini.com/)

then scroll to Broadcom Wireless Driver Fix In Lucid

and try this

It worked for me I have a Dell Mini 10

Denton Larson

Hi, I'm new to this forum and this post really helped me :) Thanks! :D

---

### Post by Elvis99 on 2010-08-03
I had such an issue after installing 9.04 on my Dell Mini 10v. I was probably more desperate then you are sam33 (no whatsoever experience with Linux and I have had 2 Netbooks to fix at that time), but then someone mentioned that through using an application named "Aircraft Manager" it was possible to turn on/off the WLAN device. 

Now, I don't know if this program runs on 10.04, but you could give it a try: 

[http://www.ubuntumini.com/2009/04/aircraft-manager-for-ubuntu-904.html](http://www.ubuntumini.com/2009/04/aircraft-manager-for-ubuntu-904.html)

---

### Post by Ozias37 on 2010-10-01
Are you still having wireless problem? I had the same problem when I installed Ubuntu 10.04 LTS desktop version on my Dell Mini 9. 10.04 does not automatically select correct driver. Your Broadcom card should use the Broadcom STA driver.Select System, then Administration, then Hardware Drivers. That will show you the selected driver-it should be Broadcom STA wireless driver. Hope this helps.

---

### Post by Cowchip7 on 2010-10-02
I would try the direction at ubuntumini.com again. Follow them to a T and you should be good to go. I did the fresh install of 10.04 on my mini 9 and wireless worked only after the driver was correctly installed.

---


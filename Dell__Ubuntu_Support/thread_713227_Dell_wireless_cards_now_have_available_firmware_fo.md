---
title: "Dell wireless cards now have available firmware for Ubuntu!"
date: 2008-03-02
forum: Dell  Ubuntu Support
---

### Post by CloudFX on 2008-03-02
Dell has recently released firmware enabling their Inspiron's wireless cards to support Ubuntu. I to had trouble doing this for about a month, until I figured this out! In fact, you can now purchase Dell computers with Ubuntu pre-installed!!

Please note that I did this on a Dell Inspiron 1521. I need feedback on whether or not this can be done other other Inspiron's, or even other Dell laptops.

Here's what to do:
1. Open up System > Administration > Restricted Drivers Manager
2. Under the firmware category, you will see something to do with a Broadcom driver. Check that box.
3. You will be prompted to either get the firmware from a disk, or to download it from a link. For me, the link was given. I believe that it will be for everyone else as well.

If you successfully get to this point, please post the default link. This way, we can assist those that are still having troubles. I will add them to this list as they are posted.

**Inspiron e1705 -** [http://xeve.de/down/wl_apsta.o](http://xeve.de/down/wl_apsta.o)


Any questions? Post here, and I'll see what I can do. Screen shots always help!

---

### Post by sdm_cacto on 2008-03-02
Dude you just made my day! i'll try the drivers as soon as i get home, can you post a Direct Link? Im havng trouble to navigate dells web site.
 
appreciate it

---

### Post by CloudFX on 2008-03-02
> **sdm_cacto said:**
> Dude you just made my day! i'll try the drivers as soon as i get home, can you post a Direct Link? Im havng trouble to navigate dells web site.
 
appreciate it

no links required. Just go to your Restricted Drivers Manager (under System > Administration), and you should see your wireless card there. Select USE, and u will be prompted for the firmware. If you select the second option, you should be able to download the firmware from a given link.

---

### Post by Gepetto on 2008-03-03
Ha, that's awesome. Ever since I reinstalled a month ago, I've been lazy to go through the whole ndiswrapper skit again, but this is just great. Thanks!

---

### Post by sdm_cacto on 2008-03-03
> **CloudFX said:**
> no links required. Just go to your Restricted Drivers Manager (under System > Administration), and you should see your wireless card there. Select USE, and u will be prompted for the firmware. If you select the second option, you should be able to download the firmware from a **given link**.
 
I know, but since my wireless connection doesnt work on ubuntu, Im gonna need some direct link or somebody to send me the new files. (that given link)
 
That would be great. thanks

---

### Post by CloudFX on 2008-03-03
The given link is given to you. It's the default you shouldn't have to select it.

---

### Post by Gepetto on 2008-03-03
> **sdm_cacto said:**
> I know, but since my wireless connection doesnt work on ubuntu, Im gonna need some direct link or somebody to send me the new files. (that given link)
 
That would be great. thanks

[http://xeve.de/down/wl_apsta.o](http://xeve.de/down/wl_apsta.o)

That's the link

---

### Post by CloudFX on 2008-03-03
Thanks, I'll add that. If anybody else does this, and they receive a different default link, then please post it so I can add it. Gepetto, what type of Dell computer are u using?

---

### Post by Papa-san on 2008-03-03
I will be installing it on at least one 1525. I'll post my experience.

---

### Post by Gepetto on 2008-03-03
I'm running an e1705, but my  wireless was being fritzy with that firmware...I dunno if it was me or the network itself. I'll have to check it out later.

---

### Post by adult swim on 2008-03-04
are you only getting 11 Mb/s with this firmware?

---

### Post by Gepetto on 2008-03-04
I was getting between 11 and 24

---

### Post by CloudFX on 2008-03-04
And is that normal for you?

---

### Post by Gepetto on 2008-03-04
That's pretty normal for the university wireless I have down here.

---

### Post by pormogo on 2008-03-04
it looks like this was already installed on my dell xps m1330n is this the ipw3495 driver? Or is this somethign else?

---

### Post by CloudFX on 2008-03-04
This is the wireless card driver. If your not having any problems connecting to the internet using wifi, you have nothing to worry about.:KS

---

### Post by wvn on 2008-03-05
Yeah, i dont think that that's the proper driver since *Broadcom corp.* refuses to release the code. But i guess if ndiswrapper doesn't work then you should settle for that.

BTW the only reason that ppl have problem installing succesfully ndiswrapper is simply because they do not place all the files included in the win.exe after extraction, just only the bcmwl5.inf driver. All the files are needed in order to work, since bcmwl5.inf has it's own dependencies.

my 2 cents (euro)

c ya

---

### Post by sdm_cacto on 2008-03-05
With the resitricted drivers on Ubuntu 7.10 for broadcom based cards (bcm43xx) your connecction is gonna be limited to 11mbps. This problem is solved with the new drivers (b43) wich are included on Ubuntu 8.04. Tomorrow Ubuntu 8.04 Alpha 6 is going to be released, im gonna try it if I have time, it comes with 2.6.24 kernel, b43 included in it.

---

### Post by CloudFX on 2008-03-05
I'll give that a go too then. Please post your results.

---

### Post by Papa-san on 2008-03-05
I went to the restricted drivers GUI and it just said I don't need any restricted drivers... Doesn't give me any further options.
```
tiffany@tiffany-laptop:~$ sudo lshw -C network
[sudo] password for tiffany:
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:44:0d:f1
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 duplex=full firmware=N/A ip=192.168.1.53 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
tiffany@tiffany-laptop:~$ 

```heres some other relavent info:```
tiffany@tiffany-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

tiffany@tiffany-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1D:09:44:0D:F1  
          inet addr:192.168.1.53  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe44:df1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2301 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1355 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1047033 (1022.4 KB)  TX bytes:205223 (200.4 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

tiffany@tiffany-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

tiffany@tiffany-laptop:~$
```EDIT:
Looks like the only way I'll be able to do it is with ndiswrapper... (The driver is bcmwl6.inf)

---

### Post by wvn on 2008-03-06
Hi all,

So, **sdm_cacto**, the new release will include all the drivers needed, therefore WiFi out-of the-box? No need for ndiswrapper or anything?

That would be great

thanx

---

### Post by sdm_cacto on 2008-03-06
I dont know for sure, but i hope so

---

### Post by MikeRussell on 2008-03-06
I have an inspiron 1420 with the dell 1390 card.  I installed Hardy alpha 6 today, updated and made sure the b43 driver was installed and in use.  Still no wifi.

Mike

When I run sudo lshw -C network I get:

   *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:a0:fc:27:7d
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=192.168.1.102 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
root@deep-thought:~# sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:a0:fc:27:7d
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=192.168.1.102 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1c:26:17:5f:49
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


The last section makes me think my card is being detected, although no wifi light is on, no wireless networks show up with 'iwlist scan' and attempting to connect with a dhcp command tells me the network is down.  Any suggestions?

---

### Post by Papa-san on 2008-03-07
THAT'S the thing that gets me...

These people (Dell) are supposedly working with the Ubuntu community. They DO have these packages available, but we cannot get our hands on them! We should be able to go to Dell support and download the proper installation .iso.

If they have an installation CD (iso) with Ubuntu on it that they send out with every Ubuntu system they sell, aren't they obligated to have this available because it is Open Source? Hell, I had my computer guy call me so I could handle his Dell/Ubuntu customers for him when they have problems. He's got a contract with them for their local service work, and he is expected to have a  Linux guy available now, but they don't even supply HIM with it!

Talk about putting a LOT of people behind the eight-ball!

Anywhoo.... If I manage to get this elusive image, am I better off to have CD's or DVD's with it? I know I am installing off of CD's I get from Canonical when I put together packages on older systems. (Which, BTW, I use ndiswrapper EXCLUSIVELY for, because the bcm43xx that's included really seems to work on almost no systems I have been exposed to...)

---

### Post by adult swim on 2008-03-07
> **MikeRussell said:**
> I have an inspiron 1420 with the dell 1390 card.  I installed Hardy alpha 6 today, updated and made sure the b43 driver was installed and in use.  Still no wifi.


The last section makes me think my card is being detected, although no wifi light is on, no wireless networks show up with 'iwlist scan' and attempting to connect with a dhcp command tells me the network is down.  Any suggestions?

my dell 1390 didnt work either with alpha 6 out of the box.  i uninstalled the b43 package in snyaptic, and then used sudo apt-get install b43-fwcutter in a terminal.  Then i went back to the driver manager, enabled it and it worked.  As pointed out in anohter thread by jw5801, you could probably just run sudo dpkg-reconfigure b43-fwcutter in  a terminal to do the same thing.

---

### Post by MikeRussell on 2008-03-07
I also got it working using a self-installed fwcutter.  I'm only getting 5Mb/s though.   Anyone getting a full 54 with this driver?

---

### Post by adult swim on 2008-03-07
It isn't possible to get 54mb/s with this firmware.  I think the max may be 24 although I am only getting 11mb/s.  This kind of sucks but it is better than being wired until ndiswrapper is working.

---

### Post by kwiwii on 2008-03-07
I have a dell inspiron E1705, I dont see anything in the restricted drivers and I have a broadcom wifi card. I think from what people have said, I will go and fiddle with ndiswrapper.

---

### Post by Papa-san on 2008-03-08
HAH! 
Got it!

[http://linux.dell.com/files/ubuntu/iso-images/](http://linux.dell.com/files/ubuntu/iso-images/)

---

### Post by CloudFX on 2008-03-08
That's great! Have you tried it yet? Also, how can you tell what speed you are getting in Mb/s?

---

### Post by Papa-san on 2008-03-09
LOL...
Not yet, as I do not have any blank cd's or dvd's to burn it to...:oops:
Fortunately, I haven't touched my other daughters laptop yet with Ubuntu. (The wife won't let me near hers until I get it figured out...) I'll (eventually) be able to see how the .iso installs... I hope it doesn't want to overwrite the whole HD... I have to keep the Win Vista OS on there...

---

### Post by CloudFX on 2008-03-13
Any news on that?

---

### Post by hogman500 on 2008-05-11
i just upgraded from the 7.10 version of ubuntu and my wireless worked because of the restricted drivers manager and it worked fine but i just installed the 8.04 version of ubuntu and the link is not there and its really annoying if someone could post a alternate way to get the same firmware i would be verry gratefull

---

### Post by wolf3491 on 2008-05-14
Before I upgrade to 8.04, what are the chances wireless will work with my Inspiron 1521?

---

### Post by huck416 on 2008-05-15
I have the 1521 and just upgraded to 8.04 from 7.10; Kubuntu actually. The upgrade well relatively well. I got my wired and wireless working with little difficulty but I am using ndiswrapper and not the restricted drivers. I've blacklisted b43. I'm getting 54mb/s at times although it usually settles down around 24-38 with a 75-80% signal. The only issue at the moment with my wireless is it won't connect at startup if my router is not broadcasting. If I allow the router to broadcast it connects fine. I'm also using the kde network manager. I've been alternating between the two kernels available to try and sort other problems but generally it's ok. Biggest frustration is the poor shutdowns - lots of errors and appears to hang. Working on that one and have found some good threads. More to follow when successful. Good luck.

---

### Post by wolf3491 on 2008-05-16
So the restricted driver doesnt work =/  I'm going to try the fwcutter for packet injection because I don't really wish to mess with ndiswrapper.  Thanks though!

---


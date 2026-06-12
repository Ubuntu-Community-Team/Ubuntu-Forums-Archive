---
title: "Wifi light doesn't work in Ubuntu 8.04 (Dell Vostro 1000)"
date: 2008-04-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by iamroot on 2008-04-29
Hey, I saw some other threads with this similar situation, but none really could help me out. 

When I did a clean install of Hardy, I noticed my Wifi light wouldn't turn on, and I can't connect to any wireless networks. I have a Dell Vostro 1000 with a Dell Wireless 1390 802.11g Mini Card. 

iwconfig produces:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"2WIRE893"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Shouldn't there be eth1? That's what always used to show up in my gkrellm monitor when I had Gutsy. Here's what I get when I try sudo ifup eth1:

```

eth1: ERROR while getting interface flags: No such device
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; No such device.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; No such device.
There is already a pid file /var/run/dhclient.eth1.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
wmaster0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up eth1.

```

---

### Post by acelin on 2008-04-30
Did it come with Ubuntu when you bought it? If so, you can probably find support on their site- they have (somewhere) repo's that deal with this sort of thing.

---

### Post by wannadumpwindows on 2008-04-30
You have to create the interface before you can bring it up. I'm not quite sure how to do it for that type of interface though. I'm used to doing it with a wireless interface.

---

### Post by mtbsoft on 2008-04-30
I have the same problem with the light on my Inspiron 9400 but my WiFi (Broadcom) works just fine.

---

### Post by iamroot on 2008-04-30
No, it didn't come with Ubuntu pre-installed. My wireless worked fine with Gutsy, only since I switched to Hardy have I had a problem with it. What are some steps I could take to try to make it work?

---

### Post by soapytheclown on 2008-04-30
well if your card is a Dell Wireless 1390 802.11g Mini Card i believe they are the same as broadcom 43XX cards, i had one in my old compaq laptop, so a forum search of either will help you :)

[http://ubuntuforums.org/showthread.php?t=769639&highlight=dell+1390](http://ubuntuforums.org/showthread.php?t=769639&highlight=dell+1390)

btw on my vostro 1700 the light itself doesnt come on but the net works fine however mine uses and intel wireless chipset.. strange that wireless is the only light not to come on though bluetooth and every other light works fine!

-edit-

just saw u posted in that thread a couple hours ago :)

---

### Post by andrewbrown22 on 2008-04-30
I used the guide shown above and it worked for my Dell Inspiron E1505 which I'd assume uses the same wireless chipset.  
Still, like others, my wireless light doesn't come on, but I do have wireless access.
It drives me crazy not having the light on though...

---

### Post by the8thstar on 2008-04-30
Same problem here, no light but wireless works on my system (Broadcom 4530).

---

### Post by biorancher on 2008-04-30
I have an inspiron 630m and I'm having the same problem as iamroot - no light and no connection.  iwconfig gives me exactly the same output too (except for the essid).

---

### Post by notwen on 2008-05-01
This will fix everyone's light using Intel 3945 wireless on Hardy:

```
sudo apt-get install linux-backports-modules-hardy
```

After this is finished, disconnect your wireless and enter the following code in a term:

```
sudo modprobe -r iwl3945
sudo modprobe iwl3945
```

Note: The drivers included in this backport only enables the wifi light, it does not blink during transfers, but lights up w/ an active connection.  Hopefully Intel will continue to update the drivers and they will find their way into a future Hardy update.

To check an see which wireless chipset you have try the following command:

```
lspci
```

Browse through the output and see if you come across a Intel or Broadcom wireless device, which would be the case w/ most Dells.  Hope this helps.  =]

---

### Post by soapytheclown on 2008-05-01
> **notwen said:**
> This will fix everyone's light using Intel 3945 wireless on Hardy:

```
sudo apt-get install linux-backports-modules-hardy
```

After this is finished, disconnect your wireless and enter the following code in a term:

```
sudo modprobe -r iwl3945
sudo modprobe iwl3945
```

Note: The drivers included in this backport only enables the wifi light, it does not blink during transfers, but lights up w/ an active connection.  Hopefully Intel will continue to update the drivers and they will find their way into a future Hardy update.

To check an see which wireless chipset you have try the following command:

```
lspci
```

Browse through the output and see if you come across a Intel or Broadcom wireless device, which would be the case w/ most Dells.  Hope this helps.  =]


confirmed that works for my iwl4965 N wireless card =D thanks for that (obv you have to sudo modprobe -r iwl4965 etc)

---

### Post by andrewbrown22 on 2008-05-01
I can confirm that this works to get the light working again.  By installing the backports and running the modprobe command I can still connect to wireless and the light finally comes on.

---

### Post by biorancher on 2008-05-02
I just booted it up and was getting ready to try the proposed fix, when I got a message that said new hardware is detected.  Then it asked if I wanted to download and install the firmware.  I did and it works great.  Nicely done, whoever did that.

---

### Post by empty_tank on 2008-05-07
i have vostro 1400n.  your solution worked to solve the wifi indicator problem.  thank u.

---

### Post by sayantandas on 2008-06-29
> **notwen said:**
> This will fix everyone's light using Intel 3945 wireless on Hardy:

```
sudo apt-get install linux-backports-modules-hardy
```

After this is finished, disconnect your wireless and enter the following code in a term:

```
sudo modprobe -r iwl3945
sudo modprobe iwl3945
```

Note: The drivers included in this backport only enables the wifi light, it does not blink during transfers, but lights up w/ an active connection.  Hopefully Intel will continue to update the drivers and they will find their way into a future Hardy update.

To check an see which wireless chipset you have try the following command:

```
lspci
```

Browse through the output and see if you come across a Intel or Broadcom wireless device, which would be the case w/ most Dells.  Hope this helps.  =]

thanks dude,
ur suggestion worked for my dell Inspiron 6400... it works gr8 now. the light is on. :guitar:

---

### Post by mtbsoft on 2008-06-30
Alas, I must sadly report that this doesn't work on my Inspiron 9400 with the Intel chipset - WiFi but no light (sigh).

---


---
title: "WiFi card gets power, Ndiswrapper sees it, but it wont connect..."
date: 2006-08-22
forum: Desktop Environments
---

### Post by nzk on 2006-08-22
I installed ndiswrapper, configured it for my wificard, and rebooted

Now the little blinking (now they are solid) lights are on, but I am not getting a connection! Why?!

---

### Post by nzk on 2006-08-22
Bump


I tried everything, and **everything is perfectly fine**

just ***it wont connect***!!

I made it DCHP and the essid the one of my router...


What is wrong?

I also noticed that only one of the lights are on on my card

---

### Post by nzk on 2006-08-22
Bump...argh this is so annoying why wont it work

---

### Post by mcarlson on 2006-08-22
We could use a little more information:

1) What chipset are you using?
You should have figured this out to add the correct .inf for ndiswrapper

2) what does 'ndiswrapper -l' tell you?

3) If you go into system->administration->Networking
does the wireless card show up?

M@

---

### Post by nzk on 2006-08-22
> **mcarlson said:**
> We could use a little more information:

1) What chipset are you using?
You should have figured this out to add the correct .inf for ndiswrapper

2) what does 'ndiswrapper -l' tell you?

3) If you go into system->administration->Networking
does the wireless card show up?

M@
1. Its a Belkin F5D8010 with some airgo chipset or something the wiki for ndiswrapper said to use some netgear card drivers, which worked


2. ndiswrapper -l returns:
Installed ndis drivers:
netani          driver present, hardware present
3. It says Wireless Connection wlan0

---

### Post by nzk on 2006-08-22
Another bump because its frustrating :(

---

### Post by nzk on 2006-08-22
3rd Bump :(

---

### Post by nzk on 2006-08-22
One last bump before I give up...

---

### Post by NetworkGuy on 2006-08-22
Please stop bumping or you won't get much help..

Open a terminal and type

```
iwlist wlan0 scan
```

This will show you the access points/routers that your wireless card sees.  Is your acccess point/router in the list?

---

### Post by nzk on 2006-08-22
> **NetworkGuy said:**
> Please stop bumping or you won't get much help..

Open a terminal and type

```
iwlist wlan0 scan
```

This will show you the access points/routers that your wireless card sees.  Is your acccess point/router in the list?

Yes

---

### Post by nzk on 2006-08-22
What does that mean then?

---

### Post by NetworkGuy on 2006-08-22
It means your wireless card is working.  Now we just have to get the card associated with the ESSID you use.

OK, go to system -> administration -> networking (You will need to enter your password)

Click on your wireless card and then click properties.

Put in the ESSID of your access point/router.  If you are using WEP, you will need to enter the hex code of your WEP key.  Click OK until you have backed out of everything.

From a terminal type ```
 iwconfig 
``` to see if your wlan0 is associated with your access point/router.  Such as 

wlan0     IEEE 802.11b+/g+  **_ESSID:"Your ESSID"_**  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:13:10:2C:15:AC
          Bit Rate:36 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=45/100  Signal level=23/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


If it is type ```
 ifconfig 
``` to make sure your wireless card has an IP address (not Inet6).  Such as

wlan0     Link encap:Ethernet  HWaddr 00:13:10:67:94:8F
          _**inet addr:192.168.1.101**_  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:10ff:fe67:948f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2451 errors:3 dropped:0 overruns:0 frame:0
          TX packets:2082 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2521015 (2.4 MiB)  TX bytes:365780 (357.2 KiB)
          Interrupt:11


Let us know where you stand after doing this.

---

### Post by nzk on 2006-08-22
> **NetworkGuy said:**
> It means your wireless card is working.  Now we just have to get the card associated with the ESSID you use.

OK, go to system -> administration -> networking (You will need to enter your password)

Click on your wireless card and then click properties.

Put in the ESSID of your access point/router.  If you are using WEP, you will need to enter the hex code of your WEP key.  Click OK until you have backed out of everything.

From a terminal type ```
 iwconfig 
``` to see if your wlan0 is associated with your access point/router.  Such as 

wlan0     IEEE 802.11b+/g+  **_ESSID:"Your ESSID"_**  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:13:10:2C:15:AC
          Bit Rate:36 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=45/100  Signal level=23/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


If it is type ```
 ifconfig 
``` to make sure your wireless card has an IP address (not Inet6).  Such as

wlan0     Link encap:Ethernet  HWaddr 00:13:10:67:94:8F
          _**inet addr:192.168.1.101**_  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:10ff:fe67:948f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2451 errors:3 dropped:0 overruns:0 frame:0
          TX packets:2082 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2521015 (2.4 MiB)  TX bytes:365780 (357.2 KiB)
          Interrupt:11


Let us know where you stand after doing this.

ifconfig returns an inet6 addr only

To be exact:
wlan0     Link encap:Ethernet  HWaddr 00:11:50:24:88:39
          inet6 addr: fe80::211:50ff:fe24:8839/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:65 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4562 (4.4 KiB)  TX bytes:0 (0.0 b)
          Interrupt:169 Memory:34000000-34080000

---

### Post by nzk on 2006-08-22
Well I have to go to sleep. I will be back online soon, please leave your answers thanks in advance :)

---

### Post by NetworkGuy on 2006-08-22
Ok, but did iwconfig have your ESSID in it?

If it did, you are associated with your access point/router but just not getting an IP address.

Are you running WEP or WPA on your access point/router?

---

### Post by mcarlson on 2006-08-23
Okay, I have to agree with NetworkGuy on a few things here.

1) The bumps make it less likely for you to get help.
We all have lives too (for me work and class).  People are happy to help but please be a little more patient with us, so we can be a little more patient with you.

2) Your card is setup correctly and working, now you just need to figure out the magic to connect to the network.

There are a few pieces to this and they ALL need to be correct AT THE SAME TIME.

a) ESSID
b) WEP/WAP key
c) Security MODE

It was the last one that messed with me and caused me to pull my hair out for 2 days (see, your not the only one)

I found that the system->admin->network tools didn't work for me.  It didn't seem to save my changes, so instead I learned to do it by hand from the command line.

these commands are your friend!
iwlist
ifconfig
iwconfig

ifconfig shows you how your network setting are configure.
this includes wired and wireless.

iwconfig shows you wireless spacific information.

'iwlist wlan0 scan' gives ou a list of the available networks.

running the commands with sudo, ie 'sudo iwconfig wlan0' will give you more information than running them without (such as your wep key setting)

You know that your card is talking to the network because it can tell you the name (essid) of the available networks through the command 'iwlist wlan0 scan'... and since you didn't tell it that information it must have gotten it from somewhere right?

This means that you've already done the hard part! 

Enough with the background, on to getting you on the network.

lets go through each piece.
1) ESSID
use 'iwlist wlan0 scan' to list the available networks
make sure to write down the EXACT essid.  It's case sensitive, so Essid is different from ESSID or essid.

2) Check to see if the wep key is enabled
looking at the iwlist scan output you should see 'Encription key:' on or off.  If it's on you will need to set the key, if its off you should just need to set the essid.

3) If the key is ON then you will also need to know the SECURITY MODE of the network, mine is 'open' but the default key setting is 'restricted'
You will need to know this setting so you can match it.

so.. now that you have all this information do this.

sudo iwconfig wlan0 essid YourEssid
** At this point if you don't have WEP/WAP skip ahead... **

** if you need to set a wep key first try this **
**if you use WAP someone else will have to help you **
sudo iwconfig key open WEPKEYHERE

** or if you got through and that didn't work **
sudo iwconfig key restricted WEPKEYHERE

** ... To here **
** if you have a wired network you probably want to put it down **
sudo ifconfig eth0 down

** now lets be extra carefull and put down the wireless one **
sudo ifdown wlan0

** then bring it back up so DHCP can give you an IP address and all that **
sudo ifup wlan0


** ALL DONE **
At this point you should have a working connection.
If not go back and try it with the other security mode..

If it still doesn't work we probably need more info, like if you are using DHCP, and if your WEP key is HEX or a string.


M@

---

### Post by nzk on 2006-08-23
> **mcarlson said:**
> Okay, I have to agree with NetworkGuy on a few things here.

1) The bumps make it less likely for you to get help.
We all have lives too (for me work and class).  People are happy to help but please be a little more patient with us, so we can be a little more patient with you.

2) Your card is setup correctly and working, now you just need to figure out the magic to connect to the network.

There are a few pieces to this and they ALL need to be correct AT THE SAME TIME.

a) ESSID
b) WEP/WAP key
c) Security MODE

It was the last one that messed with me and caused me to pull my hair out for 2 days (see, your not the only one)

I found that the system->admin->network tools didn't work for me.  It didn't seem to save my changes, so instead I learned to do it by hand from the command line.

these commands are your friend!
iwlist
ifconfig
iwconfig

ifconfig shows you how your network setting are configure.
this includes wired and wireless.

iwconfig shows you wireless spacific information.

'iwlist wlan0 scan' gives ou a list of the available networks.

running the commands with sudo, ie 'sudo iwconfig wlan0' will give you more information than running them without (such as your wep key setting)

You know that your card is talking to the network because it can tell you the name (essid) of the available networks through the command 'iwlist wlan0 scan'... and since you didn't tell it that information it must have gotten it from somewhere right?

This means that you've already done the hard part! 

Enough with the background, on to getting you on the network.

lets go through each piece.
1) ESSID
use 'iwlist wlan0 scan' to list the available networks
make sure to write down the EXACT essid.  It's case sensitive, so Essid is different from ESSID or essid.

2) Check to see if the wep key is enabled
looking at the iwlist scan output you should see 'Encription key:' on or off.  If it's on you will need to set the key, if its off you should just need to set the essid.

3) If the key is ON then you will also need to know the SECURITY MODE of the network, mine is 'open' but the default key setting is 'restricted'
You will need to know this setting so you can match it.

so.. now that you have all this information do this.

sudo iwconfig wlan0 essid YourEssid
** At this point if you don't have WEP/WAP skip ahead... **

** if you need to set a wep key first try this **
**if you use WAP someone else will have to help you **
sudo iwconfig key open WEPKEYHERE

** or if you got through and that didn't work **
sudo iwconfig key restricted WEPKEYHERE

** ... To here **
** if you have a wired network you probably want to put it down **
sudo ifconfig eth0 down

** now lets be extra carefull and put down the wireless one **
sudo ifdown wlan0

** then bring it back up so DHCP can give you an IP address and all that **
sudo ifup wlan0


** ALL DONE **
At this point you should have a working connection.
If not go back and try it with the other security mode..

If it still doesn't work we probably need more info, like if you are using DHCP, and if your WEP key is HEX or a string.


M@

Theres an ESSID (all caps) which is Stitch, the name of my network

So I put down the wired network

I did sudo ifdown wlan0, which didn't do anything as the wlan0 wasnt up at the time, then it went up and output:

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:11:50:24:88:39
Sending on   LPF/wlan0/00:11:50:24:88:39
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
bogus UDP packet length: 308
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
bogus UDP packet length: 308
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
bogus UDP packet length: 308
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
bogus UDP packet length: 308
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
bogus UDP packet length: 308
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


**Edit: Also I'm not sure what you mean by ESSID being case sensitive, because iwlist wlan0 scan returned an all caps ESSID, then I did iwconfig wlan0 essid (all lowercase) Stitch, like you said, but there was no output. I tried everything 3 times but it doesnt seem to connect. It may be the mac address problem because the router is configured to only allow certain mac addressed.**

---

### Post by nzk on 2006-08-23
Oh I forgot to mention I dont have WPA or WEP or anything encryption

Did my mac address change from when I used windows? Because if it did then that might be the problem...:\

---

### Post by nzk on 2006-08-23
Ok I found out that the mac address is the same so it cant be that...hmm :\

---

### Post by NetworkGuy on 2006-08-23
mcarlson:  Thanks for your help.

nzk: The MAC address is tied to the actual card.  It won't change unless you change cards.

> Theres an ESSID (all caps) which is Stitch, the name of my network 

The ESSID must match what you type in exactly.  Stitch is not the same as STITCH nor stitch.

I'm worried about the bogus UDP packet length errors you are getting.

Try ```
 iwconfig wlan0 essid STITCH 
``` (remember to type Stitch exactly as your access point router is setup.

If this works correctly, you should see something like:

> wlan0 IEEE 802.11b+/g+ ESSID:STITCH Nickname:"acx v0.3.21"
Mode:Managed Frequency:2.452 GHz Access Point: 00:13:10:2C:15:AC
Bit Rate:36 Mb/s Tx-Power=15 dBm Sensitivity=1/3
Retry min limit:7 RTS thr:off
Power Management:off
Link Quality=45/100 Signal level=23/100 Noise level=0/100
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0 

The ESSID should be STITCH and the Access Point should have a MAC address.   If this is true then I believe you are associated with the access point/router you have.  This needs to happen before you even try the next step.

** Next Step **

Now type ```
 sudo ifdown wlan0 
``` followed by ```
 sudo ifup wlan0 
```  You should have an IP address.   

If you get an address and can surf, let us know and we'll make one more change the a file in your system so you don't have to go through these steps everytime you boot ubuntu.

If you are associated with the access point/router but just not getting an IP address, we can try something else.

We wait to hear back from you.

---

### Post by nzk on 2006-08-23
Just to let you know, I really appreciate both your guyses help

When I type in iwconfig wlan0 essid Stitch
it returns
```
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not permitted.
```

---

### Post by NetworkGuy on 2006-08-23
I don't have my machine with me right now to see if you need sudo or not, but try ```
sudo iwconfig wlan0 essid Stitch
```

Regardless if that works or not, reply with what you get back from this command
```
iwconfig
```

---

### Post by nzk on 2006-08-23
> **NetworkGuy said:**
> I don't have my machine with me right now to see if you need sudo or not, but try ```
sudo iwconfig wlan0 essid Stitch
```

Regardless if that works or not, reply with what you get back from this command
```
iwconfig
```

sudo iwconfig wlan0 essid Stitch returns nothing

but iwconfig returns

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

wlan0     Auto  ESSID:"Stitch"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:49:80:7C:64
          Bit Rate:54 Mb/s
          Power Management:off
          Link Quality:0/100  Signal level:-58 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by NetworkGuy on 2006-08-23
:grin: 

LOL    Looking at your return of iwconfig.

Your wireless card is using ETH1 instead of WLAN0.

Try issuing the above commands to set your ESSID and then ifdown & ifup replacing WLAN0 with ETH1.

Then reply again with the output from iwconfig and ifconfig.

---

### Post by mcarlson on 2006-08-23
OOPS!  Sorry about that.  Forgot to ask if you were set up as wlan0 or eth1 (the two most likely).  Guess I should attach a warning when giving advice at midnight :-)


M@

---

### Post by nzk on 2006-08-23
Trying to do iwconfig eth1 essid Stitch returns the same error as before :\

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Stitch"  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

wlan0     Auto  ESSID:"Stitch"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:49:80:7C:64
          Bit Rate:54 Mb/s
          Power Management:off
          Link Quality:0/100  Signal level:-58 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:11:43:60:22:BE
          inet addr:192.168.1.37  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fe60:22be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:417 errors:0 dropped:0 overruns:0 frame:0
          TX packets:432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:270830 (264.4 KiB)  TX bytes:57930 (56.5 KiB)
          Interrupt:193

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:572 (572.0 b)  TX bytes:572 (572.0 b)

```

---

### Post by nzk on 2006-08-23
Also are you sure its eth1 and not wlan0? Like 100% sure?

---

### Post by jellystones on 2006-08-23
shouldn't u type

*iwconfig wlan0 essid Stitch*

?

---

### Post by nzk on 2006-08-23
> **jellystones said:**
> shouldn't u type

*iwconfig wlan0 essid Stitch*

?

I tried that many times and every time it returns
```
 SET failed on device wlan0 ; Operation not permitted.

```

---

### Post by jellystones on 2006-08-23
ok well it doesnt make sense to type 
*iwconfig eth1 essid Stitch*
because thats trying to set your wired network card to see the ssid. Try and get information on how to fix the *SET failed on device wlan0 ; Operation not permitted.* error. I can't help you with that.

---

### Post by nzk on 2006-08-23
> **jellystones said:**
> ok well it doesnt make sense to type 
*iwconfig eth1 essid Stitch*
because thats trying to set your wired network card to see the ssid. Try and get information on how to fix the *SET failed on device wlan0 ; Operation not permitted.* error. I can't help you with that.

The wired connection is eth0, wireless is wlan0 and eth1

---

### Post by nzk on 2006-08-23
Wait...is 
Sudo iwconfig wlan0 essid Stitch 
supposed to give an output? Or is it like CHMOD where there isnt an output?

**wlan0**

ifup wlan0 output:
```
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:11:50:24:88:39
Sending on   LPF/wlan0/00:11:50:24:88:39
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
bogus UDP packet length: 308
bogus UDP packet length: 308
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
bogus UDP packet length: 308
bogus UDP packet length: 308
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
bogus UDP packet length: 308
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
bogus UDP packet length: 308
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
bogus UDP packet length: 308
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

ifconfig output:
```
eth0      Link encap:Ethernet  HWaddr 00:11:43:60:22:BE
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:22034 (21.5 KiB)  TX bytes:7577 (7.3 KiB)
          Interrupt:193

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1672 (1.6 KiB)  TX bytes:1672 (1.6 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:24:88:39
          inet6 addr: fe80::211:50ff:fe24:8839/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3716 (3.6 KiB)  TX bytes:0 (0.0 b)
          Interrupt:169 Memory:34000000-34080000


```

iwconfig output:
```
lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     Auto  ESSID:"Stitch"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:49:80:7C:64
          Bit Rate:54 Mb/s
          Power Management:off
          Link Quality:0/100  Signal level:-58 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

**eth1**

ifup eth1 output:
```
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth1/00:0b:7d:13:de:65
Sending on   LPF/eth1/00:0b:7d:13:de:65
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

ifconfig output
```
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1672 (1.6 KiB)  TX bytes:1672 (1.6 KiB)

```

iwconfig output:
```
lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Stitch"  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     Auto  ESSID:"Stitch"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:49:80:7C:64
          Bit Rate:54 Mb/s
          Power Management:off
          Link Quality:0/100  Signal level:-58 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by mcarlson on 2006-08-23
Hmmmm..

How many wireless cards do you have installed???

It looks to me like you have 2 seperate drivers trying to control one wireless card.  Like bot the bcm4xx module and ndiswrapper.

That would explain both wlan0 and eth1 showing up as wireless cards.

type this:
sudo modprobe -r bcm4xx

then try to configure wlan0 again.


On the "good news" side of things..
It looks like wlan0 is connected to your access point!

wlan0     Auto  ESSID:"Stitch"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:49:80:7C:64
          Bit Rate:54 Mb/s
          Power Management:off
          Link Quality:0/100  Signal level:-58 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

See how it shows the MAC address of the access point (00:13:49:80:7C:64) that it's associated with.  You are making progress.

The other thing to check:
Link Quality:0/100
I got this when I had the WEP key set incorrectly.
Make SURE that WEP is turned off.

But.. I'm guessing at this point that it's drivers fighting it out over who controls the card.


M@

---

### Post by NetworkGuy on 2006-08-23
nzk,

Do you have 2 wireless cards in your PC?  Is the card you are using an actual card that you can remove or is it built-in to your machine?

ETH1 is where your system is saying it has found a wireless card.
> eth1      **_IEEE 802.11b/g _** ESSID:"Stitch"  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


But you can configure WLAN0 with a ESSID?

Can you reboot your PC and then reply with another iwconfig?  Rebooting resets all the iwconfig settings that everyone has asked you to do.  Doing an iwconfig immediately after a reboot should tell us where the card actually is. (WLAN0 or ETH1)

---

### Post by nzk on 2006-08-23
Ok let me try that


[B]Edit: sudo modprobe -r bcm4xx returns
```
FATAL: Module bcm4xx not found.

```[/B]

---

### Post by nzk on 2006-08-23
As a matter of fact, I do have 2 wireless cards. One inside my computer and one that plugs into the side. The 2nd one is alot better.

Upon boot iwconfig output:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

**But the strange thing is that, until I do someof those wlan0 commands, its as if wlan0 doesnt exist**


Wait a minute...ndiswrapper isnt starting upon boot. Let me try that again

---

### Post by nzk on 2006-08-23
How do I make ndiswrapper sart upon boot? Because it doesnt want to right now ...

---

### Post by mcarlson on 2006-08-23
If ndiswrapper is not being loaded at reboot, hold off and reloading it and do a 'sudo iwconfig' and see if anything shows up.  If an adapter does show up that means that the bcm43xx module (that is part of the kernel) finding an adapter and trying to use it.


Edit: sudo modprobe -r bcm4xx returns
Code:
FATAL: Module bcm4xx not found.

DOH!
that should have been:
sudo modprobe -r bcm43xx

sorry.

Hmm.. you do have 2 wireless cards.
In any case it seems that wlan0 is the one that is connecting to the accesss point, so lets work with that one for now and shut the other one down.

sudo ifconfig eht1 down


M@

---

### Post by nzk on 2006-08-23
Wow we are making lots of progress now.

Sudo iwconfig wlan0 essid Stitch works perfectly

Everything works except the link quality is 0/100, but I don't have encryption or wpa or wep or anything so I have no idea what is going on with that.

Also NetworkGuy said that he is worried about the Bogus Packet Lengths I'm getting when I do ifup, so that might be a problem.

**wlan0**

iwconfig:
```
wlan0     Auto  ESSID:"Stitch"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:49:80:7C:64
          Bit Rate:54 Mb/s
          Power Management:off
          Link Quality:0/100  Signal level:-58 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ifup output:
```
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:11:50:24:88:39
Sending on   LPF/wlan0/00:11:50:24:88:39
Sending on   Socket/fallback
andrei@andrei-laptop:~$ sudo ifup wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:11:50:24:88:39
Sending on   LPF/wlan0/00:11:50:24:88:39
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
bogus UDP packet length: 308
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
bogus UDP packet length: 308
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
bogus UDP packet length: 308
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
bogus UDP packet length: 308
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
bogus UDP packet length: 308
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by nzk on 2006-08-24
Update: I installed a program called WiFi radar, which sees the Access Point with full bars, but when I connect the terminal still shows link quality 0/100 and I can't surf or ping or anything. So now its just link quality and the bogus packet errors...

---

### Post by mcarlson on 2006-08-24
Here are my thoughts.  Take them for what they are worth.

You have a system that is more complicated than it needs to be.  It's always best to try and solve one problem at a time if possible, but we have been trying to do a bit more than that.

My suggestions.
1) Remove the second wireless card OR turn off the internal one.
Only work with one network connection at a time.  It will reduce the complexity.

2) Make sure that you do not have 2 competing drivers loaded at the same time.  That means turning off one of the two Boradcom drivers:
either...
modprobe -r bcm43xx
or
modprobe -r ndiswrapper

At this point it looks like you are closer to having things working with ndiswrapper, so I'd remove bcm43xx.

3) Take a look at your access point's configuration and note everything you can about the connection.
Is it setup for DHCP, is there a WEP/WAP key set even if WEP/WAP are turned off, what modes are set "open" "managed" "restricted" etc.

Now.. once the complexity of the problem has been reduced (1 card, 1 driver, 1 access point, known setup) you can start looking for the missing piece.

For me it was setting the security mode to "open"

Yesterday when messing with some scripts it was having a key set for the wireless card, but having WEP turned OFF on the access point ('iwconfig wlan0 key off' fixed this for me)

Both of these showed me similar results to what you are seeing (Link Quality:0/100)

You have to have all the pieces matching on both sides.


M@

---

### Post by nzk on 2006-08-24
Ok I literally took out the broadcom wireless card since its worse and I did modprobe -r bcm43xx. I made sure that the router is DHCP and there is no encryption at all there. So now its as simple as can be. Just need to find that puzzle piece ;)

---

### Post by theLowerFre on 2006-08-24
keep it up people.  
i'm having the same problem as nzk (minus the two wireless cards), and this thread looks to be quite promising in helping me figure everything out.

thanks [from the sidelines].=D>

---

### Post by nzk on 2006-08-26
Alright I am back in the US. This is a different router but its the pre-n router, which goes with the pre-n card, and I am absolutely positive the setup is the simplest possible (no encryption, DHCP, etc.) 

I still have only one wireless card (funny story about the second one actually, I put it in my pocket and you can imagine the confusion at JFK security :P)

This is what I usually do when I boot:

1.sudo modprobe -r bcm43xx
2.*reinstall ndiswrapper drivers (just remove them and add them again)*
3.sudo modprobe ndiswrapper
4.sudo iwconfig
5.sudo iwconfig wlan0 essid *myessid*
6.sudo iwconfig
7.*Try to use WiFi radar or any other programs to connect to router*
8.sudo iwconfig
9.sudo ifdown wlan0
10. sudo ifup wlan0
11. sudo iwconfig wlan0 key off
*Here I get the bogus packet errors...*
**Link Quality 0/100**


BTW, thanks theLowerFre, glad to know I'm not alone ;)

---

### Post by NetworkGuy on 2006-08-26
Hmmm..

Another shot in the dark..

```
sudo iwconfig wlan0 mode Managed
```

---

### Post by NetworkGuy on 2006-08-26
Also check out this forum link

[HTML]http://www.ubuntuforums.org/showthread.php?t=185174[/HTML]

I just found it.

---

### Post by lik3n on 2006-08-27
> **mcarlson said:**
> Okay, I have to agree with NetworkGuy on a few things here.

1) The bumps make it less likely for you to get help.
We all have lives too (for me work and class).  People are happy to help but please be a little more patient with us, so we can be a little more patient with you.

2) Your card is setup correctly and working, now you just need to figure out the magic to connect to the network.

There are a few pieces to this and they ALL need to be correct AT THE SAME TIME.

a) ESSID
b) WEP/WAP key
c) Security MODE

It was the last one that messed with me and caused me to pull my hair out for 2 days (see, your not the only one)

I found that the system->admin->network tools didn't work for me.  It didn't seem to save my changes, so instead I learned to do it by hand from the command line.

these commands are your friend!
iwlist
ifconfig
iwconfig

ifconfig shows you how your network setting are configure.
this includes wired and wireless.

iwconfig shows you wireless spacific information.

'iwlist wlan0 scan' gives ou a list of the available networks.

running the commands with sudo, ie 'sudo iwconfig wlan0' will give you more information than running them without (such as your wep key setting)

You know that your card is talking to the network because it can tell you the name (essid) of the available networks through the command 'iwlist wlan0 scan'... and since you didn't tell it that information it must have gotten it from somewhere right?

This means that you've already done the hard part! 

Enough with the background, on to getting you on the network.

lets go through each piece.
1) ESSID
use 'iwlist wlan0 scan' to list the available networks
make sure to write down the EXACT essid.  It's case sensitive, so Essid is different from ESSID or essid.

2) Check to see if the wep key is enabled
looking at the iwlist scan output you should see 'Encription key:' on or off.  If it's on you will need to set the key, if its off you should just need to set the essid.

3) If the key is ON then you will also need to know the SECURITY MODE of the network, mine is 'open' but the default key setting is 'restricted'
You will need to know this setting so you can match it.

so.. now that you have all this information do this.

sudo iwconfig wlan0 essid YourEssid
** At this point if you don't have WEP/WAP skip ahead... **

** if you need to set a wep key first try this **
**if you use WAP someone else will have to help you **
sudo iwconfig key open WEPKEYHERE

** or if you got through and that didn't work **
sudo iwconfig key restricted WEPKEYHERE

** ... To here **
** if you have a wired network you probably want to put it down **
sudo ifconfig eth0 down

** now lets be extra carefull and put down the wireless one **
sudo ifdown wlan0

** then bring it back up so DHCP can give you an IP address and all that **
sudo ifup wlan0


** ALL DONE **
At this point you should have a working connection.
If not go back and try it with the other security mode..

If it still doesn't work we probably need more info, like if you are using DHCP, and if your WEP key is HEX or a string.


M@


1. Holy crap, you're a linux god.
2. Same as #1.
3. You rule.

---

### Post by nzk on 2006-08-27
> **NetworkGuy said:**
> Also check out this forum link

[HTML]http://www.ubuntuforums.org/showthread.php?t=185174[/HTML]

I just found it.

Thanks but its not broadcom, its airgo

---

### Post by QuietRiot on 2006-09-26
I'm not sure if what I went through will help, but my card was stuck on the 'bogus udp' and I finally got it solved. A brief sequence of events:
- my wireless card was working
- I did the most recent update (I believe they were kernel updates)
- ndiswrapper no longer had my driver, reinstalled it
- any attempt to get an IP from the router/AP I got the 'bogus udp' error

I have gone through quite a bit of checking/uninstalling/re-installing and I still got the 'bogus upd'. Finally fixed it, however, my process was very ad-hoc and I'm not sure which step exactly fixed the problem.
- reset router (it's a router/AP so when I say router = router/AP)
- turned off all encryption
- turned off MAC address restriction (I'm not sure if many routers have this fuction, but my Netgear can allow you to only accept connections from certain MAC addresses - I normally have this on.)
- reset router
- (still got bogus udp)
- removed all ndiswrapper drivers ('ndiswrapper -e netani' in my case)
- turned off ndiswrapper (modprobe -r ndiswrapper)
- removed ndiswrapper (used Synaptic Packet Manager) - also removed the other 2 packages associated with it
- downloaded and installed latest stable source from SourceForge (v. 1.23)
- reinstalled driver, connected to AP (like you've done many times)
- and then 'sudo ifup wlan0' magically gave me an IP.

I have the sneaking suspition that the ndiswrapper version 1.23 was what solved the problem, but I'm not 100% sure.

By the way, thanks a lot for the info on this thread.


Some info:
Airgo card/driver (Netgear WGM511 card, WPNT511 driver [NETANI.inf])
Ubuntu Dapper Drake (kernel 2.6.15)
Compaq Armada M700 (Pentium 2)

---

### Post by Danni on 2006-09-27
It was ndiswrapper 1.23 that solved your problem. I know that as it was the only aspect of my attempts that changed :)

---


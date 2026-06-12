---
title: "Dell xps 1330: Ubuntu incredibly slow and lan connection problems"
date: 2008-02-03
forum: Dell  Ubuntu Support
---

### Post by herger on 2008-02-03
Hi all!
I am new with Ubuntu Gutsy after two years with Fedora.
I am also new in this forum, I hope this is the right place to posto my questions...
I bought the new Dell XPS 1330 and I am very happy with the exception of the usual difficulties (microphone, suspend, etc...) I am working on.

Two major problems I am not able to afford:

1) the dhcp LAN connection doesn't work whatever I try: if I put my office static IP (at work) I have no problems;

2) the pc is icredibly SLOW: to turn on it takes about 10 minutes with Gutsy (!!!!!!) and to open a 425 byte fortran text file with VIM it takes 15-20 seconds............. Can this be due to Compiz Fusion and Avant Window Navigator??

My hardware is
Core 2 Duo 2.2 GHz, 2 Gb RAM, 160 GbHD, nVidia GeForce 8400 128 Mb.

Can anybody help me? 

Thanks in advance and the best regards

Herger
__________________

---

### Post by faulkes on 2008-02-03
> **herger said:**
> Hi all!
Two major problems I am not able to afford:

1) the dhcp LAN connection doesn't work whatever I try: if I put my office static IP (at work) I have no problems;


dhcp anywhere or just at work? it's entirely possible the dhcp server is filtering based on mac address (depending on where you work and how dastardly your admins are).

Is there anything reported in /var/log/{messages,secure} about the dhcp client?

Could you list what you have tried (and outcomes) so we can better understand how to address the problem?

> 
2) the pc is icredibly SLOW: to turn on it takes about 10 minutes with Gutsy (!!!!!!) and to open a 425 byte fortran text file with VIM it takes 15-20 seconds............. Can this be due to Compiz Fusion and Avant Window Navigator??


Which driver are you using for he nvidia card?

Faulkes

---

### Post by herger on 2008-02-04
Hi!
Thanks for Your reply.
For what concerns the graphic card driver, if I open Restricted drivers itt says

Accelerated nVidia Drivers  in use      with a green light  and
Intel pro/wireless 3945 driver for Linux  in use   with the same green light.


The dhcp never works, with the excpetion of a wireless connection in one of the places I work in.
In /var/log/messages there is something strange, You are right:

 kernel: [   84.256000] Failure registering capabilities with primary security module.
 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason   (but my connection is on eth0 !!!   :confused: )
kernel: [  413.080000] ADDRCONF(NETDEV_UP): eth0: link is not ready
 kernel: [   19.450852] Failure registering capabilities with primary security module.

(these are only the strangest messages).
I tried both roaming and dhcp, I tried to put the dns domain and not, I tyried putting some dns I found on Internet with or without the dns domain and nothing at all...

This morning at work, I have my static IP and everything works: the messages are

 kernel: [   58.976000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Feb  4 09:15:40 Orion kernel: [  275.692000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb  4 09:15:40 Orion kernel: [  275.692000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Feb  4 09:15:40 Orion kernel: [  275.804000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Feb  4 09:15:42 Orion kernel: [  277.200000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Feb  4 09:15:42 Orion kernel: [  277.312000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb  4 09:15:42 Orion kernel: [  277.352000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Feb  4 09:15:42 Orion kernel: [  277.604000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Feb  4 09:15:44 Orion kernel: [  279.216000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Feb  4 09:15:44 Orion kernel: [  279.632000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Feb  4 09:15:44 Orion kernel: [  279.684000] tg3: eth0: Link is up at 10 Mbps, half duplex.

Moreover, at work, both the turning on and opening with VIM are much faster!!! 
What can it be????  :confused:  :confused:   :confused:

----------------------------------

I hope it was clear.... Thanks again and the best regards

Herger

---

### Post by faulkes on 2008-02-04
> **herger said:**
> Hi!
Accelerated nVidia Drivers  in use      with a green light  and
Intel pro/wireless 3945 driver for Linux  in use   with the same green light.


Ok, so both restricted drivers are loaded.  

> 
The dhcp never works, with the excpetion of a wireless connection in one of the places I work in.


There are two intel wireless drivers that exist for the 3945 card, I believe an OSS one and the restricted driver.  You may have better luck trying the OSS based driver, there is information on the forums about it (I can't recall exactly where, search for it).

You might also want to post the output of 

```

sudo iwlist eth1 scan

AND

iwconfig

```

Further along:

> 
In /var/log/messages there is something strange, You are right:

 kernel: [   84.256000] Failure registering capabilities with primary security module.
 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason   (but my connection is on eth0 !!!   :confused: )
kernel: [  413.080000] ADDRCONF(NETDEV_UP): eth0: link is not ready
 kernel: [   19.450852] Failure registering capabilities with primary security module.


I'm going to guess that it tried to bring up the wireless device and failed (eth1 is the wireless interface on almost every dell I have seen).  I'm not sure about
that security module message but I don't like the look of it.

> 
(these are only the strangest messages).
I tried both roaming and dhcp, I tried to put the dns domain and not, I tyried putting some dns I found on Internet with or without the dns domain and nothing at all...

This morning at work, I have my static IP and everything works: the messages are

 kernel: [   58.976000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Feb  4 09:15:40 Orion kernel: [  275.692000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb  4 09:15:40 Orion kernel: [  275.692000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Feb  4 09:15:40 Orion kernel: [  275.804000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Feb  4 09:15:42 Orion kernel: [  277.200000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Feb  4 09:15:42 Orion kernel: [  277.312000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb  4 09:15:42 Orion kernel: [  277.352000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Feb  4 09:15:42 Orion kernel: [  277.604000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Feb  4 09:15:44 Orion kernel: [  279.216000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Feb  4 09:15:44 Orion kernel: [  279.632000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Feb  4 09:15:44 Orion kernel: [  279.684000] tg3: eth0: Link is up at 10 Mbps, half duplex.

Moreover, at work, both the turning on and opening with VIM are much faster!!! 
What can it be????  :confused:  :confused:   :confused:


10mbps half duplex sounds fishy (strange) in that almost everything today is 100 capable, which makes me think it could be an auto-negotiation issue which is causing the hard wired eth0 to fail (lots of cisco gear has had issues with auto-negotiation).

So, the thing I would try next, is set your IP, if that lets you connect to the network, try to dhcp again using

```

/path/to/dhclient eth0  (usually /usr/sbin/dhclient)

```

As for the issue with opening via VIM and based upon location, I'm not really sure what to say, you may wish to look at updating to the latest nvidia drivers based on the Envy tool (again, search forums for a link to it).

Keep posting information back and I'll try to help as much as possible.

Faulkes

---

### Post by herger on 2008-02-04
Hi. The answers to the 2 questions You asked me are

sudo iwlist eth1 scan


eth1      Scan completed :

          Cell 01 - Address:
                    ESSID:",,,,,,,,"
                    Protocol: IEEE 802.11bg
                    Mode: Master
                    Channel: 11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key: off
                    Bit Rates: 1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=49/100  Signal level=-79 dBm  Noise level=-79 dBm
                    Extra: Last beacon:  88 ms ago

          Cell 02 - Address:
                    ESSID:":::::::"
                    Protocol: IEEE 802.11bg
                    Mode: Master
                    Channel: 10
                    Frequency:2.457 GHz (Channel 10)
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=45/100  Signal level=-82 dBm  Noise level=-82 dBm
                    Extra: Last beacon: 100ms ago

          Cell 03 - Address:
                    ESSID:"------"
                    Protocol: IEEE 802.11bg
                    Mode: Master
                    Channel: 11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=49/100  Signal level=-79 dBm  Noise level=-79 dBm
                    Extra: Last beacon: 116ms ago

          Cell 04 - Address:
                    ESSID:"------"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=49/100  Signal level=-79 dBm  Noise level=-79 dBm
                    Extra: Last beacon: 44ms ago

          Cell 05 - Address:
                    ESSID:"------"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=42/100  Signal level=-84 dBm  Noise level=-84 dBm
                    Extra: Last beacon: 240ms ago

          Cell 06 - Address:
                    ESSID:"-----"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=40/100  Signal level=-85 dBm  Noise level=-85 dBm
                    Extra: Last beacon: 236ms ago

          Cell 07 - Address:
                    ESSID:",,,,,,,"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=35/100  Signal level=-88 dBm  Noise level=-88 dBm
                    Extra: Last beacon: 200ms ago

          Cell 08 - Address:
                    ESSID:";;;;;;;;"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=35/100  Signal level=-88 dBm  Noise level=-88 dBm
                    Extra: Last beacon: 196ms ago

          Cell 09 - Address:
                    ESSID:";;;;:::"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=37/100  Signal level=-87 dBm  Noise level=-87 dBm
                    Extra: Last beacon: 176ms ago

          Cell 10 - Address:
                    ESSID:";:;:;"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=31/100  Signal level=-90 dBm  Noise level=-90 dBm
                    Extra: Last beacon: 4320ms ago



I've hidden addresses and ESSID for privacy, I am sorry....
______________________________________
______________________________________

iwconfig 

no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID: off/any
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated
          Bit Rate: 0 kb/s   Tx-Power:16 dBm
          Retry limit:15   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality: 0  Signal level: 0  Noise level: 0
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc:16777   Missed beacon: 0
__________________________________________________________

For what concernsa the dhcp, at home I can't set a static IP address, since my provider works just in dhcp, and I have a cable connection, not wi-fi.....
So, what can I do?

Thanks very much again and regards

Herger

---

### Post by faulkes on 2008-02-04
> **herger said:**
> Hi. The answers to the 2 questions You asked me are

sudo iwlist eth1 scan


eth1      Scan completed :

I've hidden addresses and ESSID for privacy, I am sorry....



No problem, privacy is always respected.  What I do see is alot of AP's and a
number of them using the same channel.  Given that I don't know the ESSID's have you tried to force the ESSID setting via:

```

iwconfig eth1 essid <your chosen essid>

```

I would also note that two or more of the AP's are using keys which is either WEP or WPA based, if you are trying to connect to those AP's/ESSID's you would need the key in advance.  The key can also be set using the iwconfig command (see the man page).

> 
iwconfig 

no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID: off/any
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated
          Bit Rate: 0 kb/s   Tx-Power:16 dBm
          Retry limit:15   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality: 0  Signal level: 0  Noise level: 0
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc:16777   Missed beacon: 0


See above with trying to force the ESSID to a particular AP, again, always check /var/log for additional messages from the driver.

If you can force an association with a given AP, then try to use dhclient again and see if it returns an address

```

sudo /usr/sbin/dhclient eth1

```

> 
For what concernsa the dhcp, at home I can't set a static IP address, since my provider works just in dhcp, and I have a cable connection, not wi-fi.....
So, what can I do?

Thanks very much again and regards

Herger

Without more direct knowledge of how your ISP is setup (beyond it being cable) I can't really say.  One option would be to get a linksys or netgear cable router to sit in front, allow it to act as the dhcp agent and then set internal static ip's for your laptop (but that doesn't really solve the issue).

So, lets focus on what we have more information on, that being the wireless side of things and then revisit the dhcp/lan issue.

Faulkes

---

### Post by herger on 2008-02-04
Here I am, sorry for the delay...
Excuse me, can You tell me the precise instructions of what to write in the shell, please?
I am not sure I have understood the right things...
Thanks truly much and regards

Herger

---

### Post by faulkes on 2008-02-04
> **herger said:**
> Here I am, sorry for the delay...
Excuse me, can You tell me the precise instructions of what to write in the shell, please?
I am not sure I have understood the right things...
Thanks truly much and regards

Herger

For example, if your ESSID was "sample" you would type:

```

sudo iwconfig eth1 essid sample

```

That should associate it with the specific AP (regardless of channel) with the ESSID of "sample" given that there is no key.

You can then issue a:

```

sudo /usr/sbin/dhclient eth1

```

to try to have dhcp talk to the AP to get an IP address.

Setting a key is a little more tricky as I would need to know if it's WEP or WPA, if the WPA supplicant is running or not, etc.. so for right now, unless otherwise stated, I'm assuming you are connecting to a network which does not utilize WEP/WPA.

Faulkes

---

### Post by stream303 on 2008-02-05
> **herger said:**
> I tried both roaming and dhcp, I tried to put the dns domain and not, I tyried putting some dns I found on Internet with or without the dns domain and nothing at all...

YIKES!!  If you don't know your ISP's DNS server addresses, just picking some up from the net randomly is a [I]major security issue.
[/I]
A better bet would be to use OpenDNS addresses.  They can be found at:

[http://www.opendns.com](http://www.opendns.com)

They happen to be
208.67.222.222 for primary
and
208.67.220.220 for secondary.

For security purposes, visit the site and verify, because you never know where a message like this can be stored/modified!

The easiest way to network **dhcp** for me is to** place the primary and backup dns addresses in your router's configuration page**.  While you are inside the router, change the administrator username and password.

---

### Post by faulkes on 2008-02-05
> **stream303 said:**
> YIKES!!  If you don't know your ISP's DNS server addresses, just picking some up from the net randomly is a [I]major security issue.
[/I]


A good suggestion, at this point however we have a larger issue, of getting him connected to the network via dhcp at all (and dhcp itself will likely return proper DNS information for him).

Faulkes

---


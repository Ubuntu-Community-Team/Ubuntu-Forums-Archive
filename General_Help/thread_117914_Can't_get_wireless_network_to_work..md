---
title: "Can't get wireless network to work."
date: 2006-01-15
forum: General Help
---

### Post by kuosion on 2006-01-15
Yes, I am new to Linux, so don't laugh.

So heres the deal, I have installed Ubuntu on both my Desktop computer and my Laptop computer. The wireless network works perfectly fine on my Desktop computer but it does not work on my Laptop computer. 

Problem:
I cannot connect to my wireless network with my laptop. When using GTKwifi it gives me a message that says "DHCP failed" After that it says i am connect with "Signal strength: 0%". Originally when GTKwifi scans for the networks it says i have 5 bars for my network (essid: JJLJ). Even when it says i am connected i cannot access my router firmware (192.168.1.1). Obviously there is something wrong with DHCP but i have no idea what to do.

Laptop Computer:
1: Ubuntu recognizes my network card and has driver support for it.
2: I have tried more than 1 wifi managers (GTKwifi 1.09, Madwifi-ng-current, the thing that comes with Ubuntu, but none of those work.)
3: I have tried googling for 4 hours and messing around on the laptop for 8 hours.
4: The card can see all the wireless networks around me. including mine.
5: I have tried editing the etc/network/interfaces file.
6: I have even tried reinstalling Ubuntu.
7: I do have an WEP encryption key, I am pretty sure it is right, i have retyped it a few times.

*: if i can thing of more things to add i will.



Hopefully someone out there knows what to do.

---

### Post by kuosion on 2006-01-15
Is this issue hopeless?
I think maybe my desktop with ubuntu is all that i can do, cause i mean whats the point of a laptop if it has to be wired to something?

---

### Post by jasmuz on 2006-01-15
You mentioned you are getting DHCP errors, are you running a DHCP server on your connection??

did you try manually scanning for your connection?
iwlist wlan0 scan

(Im as baffled as you are)...by the way what type of card does your laptop have and are you running Ndiswrapper with it? If so, have you tried several drivers?

---

### Post by kuosion on 2006-01-15
Yea my router has DHCP enabled.
Even though it doesnt matter because my neighbors all use unencrypted wireless, and i still get the same DHCP failed.

When i do  iwlist ath0 scan i see all the availible networks.

As for my card:
Vendor: Atheros Communications, Inc. 
Device: AR5212 802.11abg NIC
Bus type: PCI

1 moment, i am trying Ndiswrapper.

---

### Post by kuosion on 2006-01-15
While i am looking at this Ndiswrapper, Can you think of any other way i could go about this? This is highly unfortunate.

---

### Post by BathroomNinja on 2006-01-15
[QUOTE=kuosion]While i am looking at this Ndiswrapper, Can you think of any other way i could go about this? This is highly unfortunate.[/QUOTE]


I had a bear of a time trying to get wifi working on a friend laptop with WEP.  I had to manually enter in the 128bit WEP key in LOWERCASE into my router.  Then, I had to do the same into ubuntu using the 'networking' program.  I also could not get it to work with DHCP, so I manually set the IP to an accepted address, high up in the 80's (just wanted to make sure it never conflicted with any DHCP client).  I then had to enter in the DNS server info (address of your router).  Finnaly, after a reboot, everything was working great.

---

### Post by Monkey_See on 2006-01-15
Hello kuosion,

I have a wireless card with the same chipset, and I had no luck with the ubuntu wireless applet, or the various connection managers.  Here is how I connect, maybe it will work for you also.

I am assuming that you have an onboard nic that is eth0, and your wireless is ath0, you might have to change these to suit your system.

```

sudo ifconfig ath0 down

sudo ifconfig eth0 down

sudo iwconfig ath0 channel **your_channel**

sudo iwconfig ath0 essid **your_essid**

sudo iwconfig ath0 key **your_key**

sudo ifconfig ath0 up

sudo dhclient ath0

```

If this works for you a convient way is to put these into a script a run them when you want to connect to your network.

---

### Post by kuosion on 2006-01-15
Ok, Lemme try BathroomNinja's method first.
[OK this did not work]
[thank you for your input though :)]


Then if that does not work i will do your manual commands
[Ok this did not work either]

---

### Post by mscman on 2006-01-15
[QUOTE=Monkey_See]Hello kuosion,

I have a wireless card with the same chipset, and I had no luck with the ubuntu wireless applet, or the various connection managers.  Here is how I connect, maybe it will work for you also.

I am assuming that you have an onboard nic that is eth0, and your wireless is ath0, you might have to change these to suit your system.

```

sudo ifconfig ath0 down

sudo ifconfig eth0 down

sudo iwconfig ath0 channel **your_channel**

sudo iwconfig ath0 essid **your_essid**

sudo iwconfig ath0 key **your_key**

sudo ifconfig ath0 up

sudo dhclient ath0

```

If this works for you a convient way is to put these into a script a run them when you want to connect to your network.[/QUOTE]

someone correct me if i'm wrong, you should be able to run the iwconfig commands at the same time separated by spaces i.e.:
```
sudo iwconfig ath0 channel **your_channel** essid **your_essid** key **your_key**
```

of course you would probably want to put this in a script if you have to do it more than once.:D  just trying to save you some time (and typing...) ;)

---

### Post by kuosion on 2006-01-15
> sudo ifconfig ath0 down

sudo ifconfig eth0 down

sudo iwconfig ath0 channel your_channel

sudo iwconfig ath0 essid your_essid

sudo iwconfig ath0 key your_key

sudo ifconfig ath0 up

sudo dhclient ath0

```

kuosion@jlaptop:~$ sudo dhclient ath0

Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/ath0/00:0b:cd:5a:91:52
Sending on   LPF/ath0/00:0b:cd:5a:91:52
Sending on   Socket/fallback
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 21
No DHCPOFFERS received.
Trying recorded lease 192.168.1.109
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

```



That didnt work. I had 100% packet loss.

Things are not going too well.

---

### Post by Monkey_See on 2006-01-15
kuosion,

What format is your wep key? (plain or hex)

If it is plain, I think you might have to put "s:" before your key.

---

### Post by kuosion on 2006-01-15
> kuosion,

What format is your wep key? (plain or hex)

If it is plain, I think you might have to put "s:" before your key.


Its Hex

---

### Post by kuosion on 2006-01-15
Actually, Im gonna try removing the wep key for a few moments too see if i can connect.

If that still doest work then we are going to have to approach this a different way.
[In conclusion: That did not work.]



Perhaps, its time to work Ndiswrapper, althought im am sure this wont help. Doesnt Ndiswrapper let you use windows drivers? If so then how would Ubuntu's driver setup be any different?

I may be wrong. Maybe for some reason the driver i am using already will not query the DHCP correctly.

---

### Post by Lambert on 2006-01-15
Couple questions

1. You said you're using wep. What kind of settings ascii or hexa key? open or shared key?
2. Have you checked if you have router association

Post output of these commands

arp -a
iwconfig

---

### Post by kuosion on 2006-01-15
I am using Hex key, and it is shared.


arp -a
did not return anything. it just went to the next command line.


```

kuosion@jlaptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"JJLJ"
          Mode:Managed  Frequency:5.765 GHz  Access Point: 00:13:10:E3:D2:64
          Bit Rate:6 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:6  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:1   Missed beacon:7

sit0      no wireless extensions.

```






BTW, is there an IRC channel or something i can join for faster response?
I have wasted 2 good days of my life on this thing, just hoping to speed the process.

---

### Post by Lambert on 2006-01-15
try these commands in the same order

sudo ifconfig ath0 down

sudo ifconfig ath0 up

sudo iwpriv ath0 authmode 2

sudo iwconfig ath0 essid ___ key ___

if you know your ap mac address you can add to the end of the iwconfig command 



ap __:__:__:__:__

then 

sudo dhclient ath0

there are ubuntu irc channels you can go to #ubuntu #ubuntuforums on freenode

I'll also stick around for the next 1/2 hour and watch this thread.

---

### Post by kuosion on 2006-01-15
```

kuosion@jlaptop:~$ sudo ifconfig ath0 down
Password:
kuosion@jlaptop:~$ sudo ifconfig ath0 up
kuosion@jlaptop:~$ sudo iwpriv ath0 authmode 2
kuosion@jlaptop:~$ sudo iwconfig ath0 essid JJLJ key XXXXXXXXXXXXXXXXXXXXX
kuosion@jlaptop:~$ sudo dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 14965
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/ath0/00:0b:cd:5a:91:52
Sending on   LPF/ath0/00:0b:cd:5a:91:52
Sending on   Socket/fallback
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
Trying recorded lease 192.168.1.109
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 1.783/1.783/1.783/0.000 ms
bound: renewal in 28489 seconds.

```

```

kuosion@jlaptop:~$ sudo dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 21442
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/ath0/00:0b:cd:5a:91:52
Sending on   LPF/ath0/00:0b:cd:5a:91:52
Sending on   Socket/fallback
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
Trying recorded lease 192.168.1.109
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

```

I tried it 2 times. The first time it worked the second time it didnt.

[LIST]
[*]The first time i had eth0 active because i was contacting these forums, so maybe thats why it worked.
[*]The second time i turned off eth0 to see what would happen and ath0 failed to ping or contacting DHCP.
[/LIST]



Its getting late over here. Im going to continue my quest tommorow. Hopefully people will leave good advicee for me to try.

---

### Post by Lambert on 2006-01-15
Ok, one last suggestion, run the iwpriv command before the ifconfig ath0 up command.

With the madwifi driver and shared key it has to be in the right mode and it's possible it needs to be run before bringing device up.

---

### Post by kuosion on 2006-01-16
Ok, So that didnt work either... :(
Im gonna mess around some more... 
Hopefully more people can try and figure out what is wrong with this thing.

I am going to try to Clean Reinstall Ubuntu once more.

Wish me luck,

---

### Post by trubblemaker on 2006-01-18
I'd really go over to the NDIS wrapper world.
Here's a link on a [howto for the graphical way]("http://ubuntuforums.org/archive/index.php/t-85378.html")
But here's the it works [everytime way.]("http://www.ubuntuforums.org/showthread.php?t=112526&highlight=ndiswrapper+howto")
Another person with [your card ]("http://www.ubuntuforums.org/showthread.php?t=91732&highlight=ndiswrapper+howto")

there's also native support for the drivers, but It's not on 100% yet so I wont suggest it. (I had the same issue as you and havent been able to resolve it.)

---


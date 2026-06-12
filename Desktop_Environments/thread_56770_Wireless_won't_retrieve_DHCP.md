---
title: "Wireless won't retrieve DHCP"
date: 2005-08-14
forum: Desktop Environments
---

### Post by desertViking on 2005-08-14
Hi,

I've been bouncing back and forth between 5.04 and Mepis.  Mostly, I've spent my time in Mepis because it has provided a service that I have not yet been able to activate using ubuntu.  I truly hope you can help me because this seems to be a much more professional distribution.

Anyway, here it is.  

I have wlan0 attached to a wireless card.  I have gone so far as to run ifup, ifdown, iwconfig and scanning from the command line.  WEP is enabled on the wireless router.  The router ID and WEP key are configured in the proper configuration file.  

When scanning the network, I find all of the relevant wireless networks in my neighborhood just fine, so I know it is recognizing the card and my router.  I have the connection configured for DHCP.

When I try to bring the network up, the connection will scan a series of ports, then timeout saying that it has failed to receive a response from the network.

Couple of interesting things.  I sometimes see the connection point on the router.  So, I know that I'm getting to the router box.

I tried copying the configuration file from the mepis installation (which works).  They also take advantage of a series of scripts which are not on the ubuntu distribution.  These are beyond my capability to understand at this point.

If someone thinks they have an idea, I'd love to do some screen shots and send you exactly what I am seeing.

Again, than you for your patience.

---

### Post by heimo on 2005-08-14
When you run iwconfig do you see that you have wlan0 interface, but it doesn't have ip address or other settings? I'm not certain, but on wired network you would type sudo dhclient eth0, in your case probably sudo dhclient wlan0 to invoke DHCP client. Is that the part that timeouts without success? What's the exact message this gives to you? When successull, it should be something like: DHCPREQUEST on wlan0 to 255.255.255.255 port 67, DHCPACK, bound to xxx.xxx.xxx.xxx -- renawal in yyyy seconds.

---

### Post by desertViking on 2005-08-15
Hi,

It's been a bit before I could get back to you.  Getting information from the ubuntu installation is a bit tedious since I have to connect to the network by rebooting.

Ok, so I logged on to the ubuntu distribution and started a kernel console.  I ran iwconfig wlan0 and ifup on the same port.  These are the results:

--------------------------------------------------

root@ubuntu1:/etc # iwconfig wlan0 
wlan0     IEEE 802.11g  ESSID:"xxxxxx"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:09:5B:C5:60:CE
          Bit Rate:54 Mb/s   Tx-Power:10 dBm   Sensitivity=0/3
          RTS thr:4096 B   Fragment thr:4096 B
          Power Management:off
          Link Quality:100/100  Signal level:-39 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@ubuntu1:/etc # ifup wlan0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0f:b5:09:19:29
Sending on   LPF/wlan0/00:0f:b5:09:19:29
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 --------------------------------------------------

Again, I know that the wireless router is configured correctly because I can attach using the other distribution and an XP laptop.  

Any advice?

Kind regards,

desertViking

---

### Post by buldir on 2005-08-15
I was having the same problem.  It seems the wireless settings are not being saved (or properly read) from the wifi config file.  The only way I got reliable results was to run a script after booting up.  I got this from another post:

```
## wireless-tools Configuration Script
##
## I wrote this script because I couldn't find where
## wireless-tools (iwconfig, etc.) stores its information.
## And, since the information wasn't being remembered after
## a reboot, this script was designed to fix that.
##
## - Philip Cain (philipacamaniac@gmail.com)
## Wireless Interface (the card you want to use)
IFACE="wlan0"
## Wireless Network SSID
ESSID="put your ssid here"
## Wireless Encryption (WEP) Key
## 128bit key format: xxxx-xxxx-xxxx-xxxx
## 64bit key format: xxxxxxxxxx
KEY="put your key here"
## Default Gateway (if you have set a static IP)
GW="192.168.1.1"
echo "Connecting to wireless network..."
iwconfig $IFACE essid $ESSID key $KEY
## Uncomment this line to set the gateway
#route add default gw $GW $IFACE
```

I also added to the end of the script:

```
ifup $IFACE
```

Run this with sudo, or run the script as an init script to automatically run it at boot up.  You could create a similar script to shut the wifi down:


```
ifdown wlan0
modprobe -r "name of wifi driver"
```

---

### Post by desertViking on 2005-08-15
Hey, thanks for the reply.  I'll give this a try when I get home.

BTW, I am uncertain as to where to install the script so that it executes at boot-up.  I know there's a standard reference.  Can you remind me?

Thx again!

---

### Post by buldir on 2005-08-15
Try this:

[http://www.fperkins.com/HowToCreateaStartupScriptinDebian.html](http://www.fperkins.com/HowToCreateaStartupScriptinDebian.html)

---

### Post by desertViking on 2005-08-19
Hi,

I've tried the suggestions you gave (thank-you).  I've had not luck so far.

When I execute the route add command, I get :

SIOCADDRT: Network is unreachable

When I execute the ifup script, I get the same results as before.

With your suggestions, the configuration still does not appear to retrieve the proper access point.  :

wlan0     IEEE 802.11g/b+  ESSID:"xxxxLNET"  Nickname:"***"
          Mode:Auto  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:1 Mb/s   Tx-Power:15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Encryption key:xxxx-xxxx-xx   Security mode:open
          Power Management:off
          Link Quality:36/100  Signal level:11/100  Noise level:0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

It still does not seem to want to retrieve a DHCP access point.

I did get the system to sort of connect to the wireless router by using gtkwifi.  That seems unrepeatable though.  When it was up for a few minutes, I could see the IP address as all zeros, as was the device name.

Any advice?

---

### Post by buldir on 2005-08-19
Are you using WEP or WPA?  If WEP, your KEY is:
```
KEY=xxxx-xxxx-xx
```
without quotes if you put it in this format.  From what I understand, the quotes are used when entering the text equivalent.  Make sure the wifi driver is loaded, then at the command line try:
```
iwconfig wlan0 essid "essid_name" key xxxx-xxxx-xx
dhclient wlan0
```
Any luck?

---

### Post by desertViking on 2005-08-19
Hey,

I tried the alternate WEP id format you suggested and it did not help.  Thx for the suggestion.  As it turns out, I had just placed x's where the number would appear in my e'mail thread.  When I checked the ID in both cases, it was OK.

It's a puzzle.  As I write this, I'm booted to the other OS and attached to the wireless card.

Thx for hanging in there with me.  I'd really like to get this working.

Regards

---

### Post by chrisod on 2005-08-19
Have you looked at this thread?
[http://ubuntuforums.org/showthread.php?t=49148](http://ubuntuforums.org/showthread.php?t=49148)

I was having connections issues too and the wireless connectionmanager applet in that thread solved the problem.

---

### Post by desertViking on 2005-08-19
Hi,

Yes, actually I did.  I had some wierd experiences with it.

For some reason, it ran *really* slow on my system, a minute or there abouts just to switch between tabs and so forth.

It was able to recognize the access points on the network (the ubuntu network manager could too, to be fair), and accepted my WEP key for a connection.  

For some reason, though, I was still unable to use the connection.  In checking the iwoconfig after using gkkwifi, the access point was filled in correctly.  "ifdown" and "ifup" from that point behaved as before and would go to sleep after failing to get a DHCP access point.

Strange.

Thanks very much for replying to my queary.

---

### Post by desertViking on 2005-08-29
Yes, I tried this and it did not help.

I was wondering how to tell which driver is supporting the card at boot.  It's happened automatically.  I wonder if it's the same as the other distributions, but honestly I don't know how to check there, either.

Can someone tell me how to check which driver is loaded that is supporting a particular piece of hardware?

Thx!

---

### Post by buldir on 2005-08-29
[QUOTE=desertViking]Yes, I tried this and it did not help.

I was wondering how to tell which driver is supporting the card at boot.  It's happened automatically.  I wonder if it's the same as the other distributions, but honestly I don't know how to check there, either.

Can someone tell me how to check which driver is loaded that is supporting a particular piece of hardware?

Thx![/QUOTE]

lsmod

---

### Post by desertViking on 2005-09-18
Hi,

I write this from my fresh 5.10 beta install, having finally addressed the problem of my wireless connection. 
 \\:D/ 

Most of what I needed was here:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu)

In short, the WG311 from Netgear comes in two flavors.  The installation of Ubuntu incorrectly identified the chipset on the card, and used the 'common' driver.  Unloading it, and loading the Netgear 2.0 drivers with ndiswrapper has basically solved the problem.

Thought there might be those who were interested.

Kind regards.

---


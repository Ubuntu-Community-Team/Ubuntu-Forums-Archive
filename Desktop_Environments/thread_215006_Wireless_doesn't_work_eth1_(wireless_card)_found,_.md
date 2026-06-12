---
title: "Wireless doesn't work: eth1 (wireless card) found, but won't configure, activate"
date: 2006-07-13
forum: Desktop Environments
---

### Post by MikeBenza on 2006-07-13
I have a Netgear branded wireless card, WG511 (PCMCIA).  Ubuntu detects that I've got it and it's a wireless card, but Sytem -> Networking says that "The interface eth1 is not configured."  The Device manager sees the card and doesn't seem to report any problems with it.  When I take out the card, the device manager doesn't see it, and the wireless connection isn't an option in System -> Networking.

The card has two LEDs (green and orange), though I can't seem to remember if one was normally lit while the card was in but not being used.  Only ifconfig -a (not plain ifconfig) shows eth1, but it doesn't have any activity (nothing transmitted or received).

When I go to System -> Networking, if I choose the wireless connection, eth1, and click properties, I can activate it and set the wireless key (yes, I typed it correctly), as well as choose DHCP.

When I finish with the properties, System -> Networking says "The interface eth1 is not active."  ifconfig -a shows the same thing as before.  If I click activate it says "Activating interface 'eth1'"  and does that for a minute or two.  It then says "The interface eth1 is active.," even though eth1 is still listed only in ifconfig -a, and not ifconfig

The wireless LAN assistant can't find any APs (yes, my wireless does broadcast).

Any clue what might be wrong?


P.S. I'm on a fresh install of Dapper.
P.P.S. The wireless encryption is WEP, not WPA, so I don't think [this](http://www.ubuntuforums.org/showthread.php?t=90450&highlight=wg511) would apply even if I was on Breezy)


- Mike

---

### Post by cptnapalm on 2006-07-13
What's in your /etc/network/interfaces and are you using the Gnome Network Manager?

---

### Post by MikeBenza on 2006-07-13
> **cptnapalm said:**
> What's in your /etc/network/interfaces and are you using the Gnome Network Manager?

```

mike@ubuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

I was using KDE's network manager, but I can switch to GNOME.

---

### Post by orb9220 on 2006-07-13
In mine to get the network manger to work somebody told me to comment out all 
but the auto lo and iface lines,

when I left just that line and comment out all the eth and wlan and ath's and 
logoff then back in walla-bango it worked!

Hope this helped

---

### Post by MikeBenza on 2006-07-13
> **orb9220 said:**
> In mine to get the network manger to work somebody told me to comment out all 
but the auto lo and iface lines,

when I left just that line and comment out all the eth and wlan and ath's and 
logoff then back in walla-bango it worked!

Hope this helped

No such luck.  All that did was mark all my connections as unconfigured.  It doesn't seem like the card is even being accessed: I tried the card in a second laptop running WXP and one of the LEDs flashes while searching for wireless networks.  That doesn't happen on my dapper laptop.

- Mike

---

### Post by gratefultux on 2006-07-13
What output does iwconfig give you?

---

### Post by MikeBenza on 2006-07-13
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      NOT READY!  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Tx-Power=31 dBm   Sensitivity=0/200
          Retry min limit:0   RTS thr=0 B   Fragment thr=0 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


Hrmm...I think NOT READY! is my problem...

---

### Post by gratefultux on 2006-07-13
Hmm...ok, try
iwconfig eth1 essid [YOUR ESSID]
iwconfig eth1 mode managed
iwconfig eth1 key [ENCRYPTIONKEY]

The encryption key should be hex, meaning the letters it uses can only be A-F

And if you're in the US your channel is most likely 6, so if the above still didn't work try:
iwconfig eth1 channel 6

although i always get error messages trying to set my channel.  It usually autodetects once it finds the access point.

---

### Post by MikeBenza on 2006-07-13
All those needed to be sudo'd.  Here's the new output of iwconfig:
```

mike@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      NOT READY!  ESSID:"linksys"
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Tx-Power=31 dBm   Sensitivity=0/200
          Retry min limit:0   RTS thr=0 B   Fragment thr=0 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I found [this thread](http://www.ubuntuforums.org/showthread.php?t=156228), so I'm trying it out.

---

### Post by flosofl on 2006-07-13
> **MikeBenza said:**
> ```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      NOT READY!  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Tx-Power=31 dBm   Sensitivity=0/200
          Retry min limit:0   RTS thr=0 B   Fragment thr=0 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``` 

Hrmm...I think NOT READY! is my problem...


Well, this site shows it as supported (kinda):
[http://linux-wless.passys.nl/query_part.php?brandname=Netgear](http://linux-wless.passys.nl/query_part.php?brandname=Netgear)

Do you have the v2?  It states that it's not supported natively.  If that's the case you may want to use ndiswrapper.

I ended up having to use that with my Hawkings cards (2 PCMCIA, 1 PCI) and they work great.  WPA2 and everything.  I was having the same issue, and rather than beat my head against the wall, I gave up after a couple days and used ndiswrapper.  

I did have to put the acx module in the blacklist so it wouldn't load and stop ndiswrapper from finding the card(s).  You may have to do the same for the Prism module being loaded (is it orinoco?)

---

### Post by MikeBenza on 2006-07-13
Woohoo....it works.  Thank you for your help anyway...Without it I wouldn't have searched for Intersil 3890, another name for the card....and that's how I found the thread.

Thank you very much.

- Mike Benza

---


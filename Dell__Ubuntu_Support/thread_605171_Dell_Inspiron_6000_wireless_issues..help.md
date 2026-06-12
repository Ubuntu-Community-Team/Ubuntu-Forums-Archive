---
title: "Dell Inspiron 6000 wireless issues..help"
date: 2007-11-06
forum: Dell  Ubuntu Support
---

### Post by thisbeadam on 2007-11-06
I have a dell inspiron 6000. Everything works fine - but wireless. It acts as if the wireless adapter works, but it will not see any networks in range NOR will it manually connect. I absolutely know that I am doing everything right with the wireless part- as in wep security, ssid, etc..

That being said I have a internal  Intel Corporation PRO/Wireless 2200BG Network.
(as said by terminal using lspci -nn | grep Network)

Either way, It absolutely will not connect manually, nor will it find any networks. No matter where I go.

And its a laptop, with a brand new battery.. I need my wireless!

I have gusty running on it. At this point I complete reinstall is not what I choose to do, unless that is my only option.

Ill check other posts but I have yet to find something to fix my problem.

And I downloaded the Intel drivers for this wireless adapter for linux but It has  yet to work. I have a decent amount of linux knowledge, but clearly not enough!

HELP!
(please.)

---

### Post by mpierce on 2007-11-07
You didn't tell me which adapter your wireless card is so, I going to assume that it is eth1 since eth0 is probably the lan. You will need to set it up manually in /etc/network/interfaces. Here's the ticket for you to figure it out:

 The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
# eth1
auto 00:0E:35:EB:A9:7F  #id eth1 MAC
# eth0
auto 00:11:43:6F:7A:FA  #id eth0 MAC

iface eth0 inet dhcp

# The primary network interface
auto eth1
iface eth1 inet dhcp
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid BiPAC_7402GL   #name of my router
        wireless-key1 10c51axxxxxxxxxx   #my 128bit WEP password

Hope this helps...

---

### Post by dward526 on 2007-11-07
what network manager are you using.  I have had the native gnome work on some laptops and not on others, and wicd vice versa.  It is worthwhile to try different mangers.

---

### Post by thisbeadam on 2007-11-07
Its internal. And I got it. I'm not sure how and this might just make me sound dumb, but somehow the hardware based wireless switch was shut off. As in you press function + F2 (for mine..) 

I read someone else's post after posting this and someone wanted the Wifi light on their dell to work, and that led me to remember about the hardware switch. 

But thank you for replying.

---

### Post by MyR on 2007-11-07
that's what i was about to suggest ;]

I hope Ubuntu works out well for you!

peace

---


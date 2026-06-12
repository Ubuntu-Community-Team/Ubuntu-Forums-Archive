---
title: "firefox/wireless not connected on 1420"
date: 2007-08-26
forum: Dell  Ubuntu Support
---

### Post by eisenstein on 2007-08-26
I have a 1420N with Ubuntu 7.04 preinstalled.  When I'm in range of wireless, the connection is established ok, (e.g.  "Wireless connection to 'wsunexus' (86%)) but when I launch firefox I can't connect to any web sites- it just hangs and eventually times out.

I tried typing in the server directly (e.g. [http://64.21.33.9/](http://64.21.33.9/)) but the same thing happened.  Also tried searching for a similar thread in the forums, but couldn't find this problem.  Anyone have an idea what I should do?

---

### Post by sebald on 2007-08-26
On my straight 1420 with Gutsy, I find I have to disable and re-enable my wireless to make it get an IP address on startup. Annoying but true.

---

### Post by jay4e on 2007-08-27
can you run other internet services beyond firefox? such as apt-get update?  if its just firefox its likely you just need to reinstall.

if its a problem with the internet it could be either the access point blocking due to security (wep/wpa, MAC, ect).  or you may just need to estabilish an ip try runing from command line: ```
sudo dhclient 
```

---

### Post by deserthowler on 2007-08-27
I don't know if this will help, but I have this problem with EVERYTHNG Mozilla on Debian and Ubuntu.  I found I need to go into Firefox and turn off ipv6 everytime.  I can ping yahoo but not find it in firefox.

Earl

---

### Post by eisenstein on 2007-08-28
Still not having any luck getting firefox to connect through the wireless connection.  When I ping yahoo.com from a shell I get this:

$: ping yahoo.com
PING yahoo.com (66.94.234.13) 56(84) bytes of data.
--- yahoo.com ping statistics ---

where it hangs until I kill it.  I don't know much about this stuff- if it can resolve yahoo.com to 66.94.234.13, does that mean it's getting out to somewhere, or is that info already contained on the laptop?

When I try sudo dhclient here's what I get:

$: sudo dhclient

Listening on LPF/eth1/00:1b:77:9c:df:bf
Sending on   LPF/eth1/00:1b:77:9c:df:bf
Listening on LPF/eth0/00:1a:a0:fe:42:c4
Sending on   LPF/eth0/00:1a:a0:fe:42:c4
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 172.16.223.254
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 172.16.223.254
bound to 172.16.223.15 -- renewal in 2858 seconds.

What does all that mean in terms of my problem?

How do I turn off ipv6?  Is that a hack of the system, or a reasonable setting to change?  The file where it can be turned off (/etc/modules.conf) says not to edit it directly, and the alternative given  (update-modules) is listed as obsolete in the man pages.  

Should I move this thread over to Networking and Wireless?

Ben

---

### Post by deserthowler on 2007-08-29
in the address box of firefox type

 about:config

and hit the goto arrow.

There will appear a blank box labeled filter.  type

ipv6

ipv6 disable should appear as false. right click and then click toggle so it appears as true.

Earl

---

### Post by eisenstein on 2007-09-04
Just an update- this wasn't a problem with Ubuntu or Dell.  My wireless worked with Firefox "out of the box" on a different wireless hotspot.  The problem came from the university wireless system I was trying to use- they require a "VPN client" to access their system.  And they provide  instructions to get it for Ubuntu.

---


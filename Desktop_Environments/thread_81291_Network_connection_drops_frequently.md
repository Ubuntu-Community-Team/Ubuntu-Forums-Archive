---
title: "Network connection drops frequently"
date: 2005-10-24
forum: Desktop Environments
---

### Post by geokker on 2005-10-24
My network connection drops very frequently on Breezy and I don't know how to troubleshoot it.

It seems to be just a hiccup - enough to chuck me out of AIM/MSN and SSH sessions - otherwise it is not noticable.

Unfortunately, I rely on an uninterrupted connection and will have to ditch Ubuntu fairly shortly unless I can get to the bottom of the problem.

I have a wifi pcmcia and a built-in nic on a Dell lappy. I never had a problem with Hoary. I can remove the wifi card and experience the same problems with the nic.

I've tried dhcp and static. 

I've eliminated the router and net connection with another PC.

I've removed the dhcp client.

Pings to net addresses run indefinitely with contiguous ICMP sequence numbers.

I've tried GAIM & Kopete with the same results.

I get:

Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7

in the syslog but nothing in any other log to suggest a problem.

Once again, there doesn't seem to be a problem with networking generally - just that I'm disconnected/reconnected every 15-20 mins or so.

Does anyone have any ideas? Can anyone give me some pointers at what I should be looking at?

---

### Post by migueljacq on 2005-10-24
Don't have a solution but I had a similar thing when I was running Firestarter. Every 15 min or so.

---

### Post by Marrea on 2005-10-24
I'm using Breezy on an Asus Barebone Desktop with an onboard Ethernet adapter and a cabled Netgear router.  I too lose the connection at regular intervals.  I can type [www.google.co.uk](www.google.co.uk) into the browser and get in and surf around a bit.  Then all of a sudden when trying to navigate to another site, I get an error about "www.[name of site].co.uk not found.  Check name and try again".  If I keep on trying, on about the fourth or fifth time it will connect again.  I'm wondering if it's something to do with my onboard NIC.

I have problems also with WinXP on the same machine - every so often I get a message in the System Tray which says "a network cable is unplugged".   But funnily enough I have no problems at all with SuSE 9.3 (the third o.s. on the computer).

---

### Post by davebgimp on 2005-10-24
[QUOTE=migueljacq]Don't have a solution but I had a similar thing when I was running Firestarter. Every 15 min or so.[/QUOTE]

Exact same thing with me, running Firestarter and using GAIM. I would get booted about every 15 minutes.

After a recent Firestarter update, this no longer happens to me.

---

### Post by migueljacq on 2005-10-24
That's right - since I reinstalled Firestarter, I've had no problems since

---

### Post by geokker on 2005-10-31
I still haven't found a solution for this. 

I don't have firestarter installed.

I have a sneaking suspicion that this is a widespread problem with a standard installation of Breezy that most people don't notice.

---

### Post by Spug on 2005-10-31
Indeed, I also often have this problem. PCI Wi-Fi card. I never gave it much thought (mainly because it just throws me off MSN Messenger, but not IRC (I get a lag that rises slowly until the connection is established again, but it doesn't last long enough to ping timeout me), thought that it was just because I lost the Wi-Fi connection for a short time, but that's not plausible as the reception is at 97 close to all the time. Strange.

---

### Post by geokker on 2005-11-21
I have replaced an Intel wifi router with a d-link wifi router and the problem has gone away. I'm willing to blame Intel for this overly generous dollop of stress paste.

---

### Post by planetcall on 2005-11-21
Same problem with me too. I am using PPPOE for my ADSL connection. The connection drops frequently. I used pppoeconf to configure the dsl and then use pon dsl-provider to start and poff to stop it. every now and then I have to do it else the connection drops. :(

---

### Post by Stambo00 on 2005-11-21
Thought I would add my grief too, as I am also experiencing this issue.

[http://ubuntuforums.org/showthread.php?t=90092](http://ubuntuforums.org/showthread.php?t=90092)

[http://ubuntuforums.org/showthread.php?t=92243](http://ubuntuforums.org/showthread.php?t=92243)

---

### Post by planetcall on 2005-12-01
By gathering some information over the issue I installed firestarter firewall using apt-get. The problem is that the firewall is blocking all my network connections. I am not a networking pro so I was not able to figure out the problem. I tried to make some rules so as to allow all connections from my adsl modem but it all failed. So I have to browse the internet without firewall and with the same frequent dropping problem. I also tried to dpkg-reconfigure but it too didnt work.:(  MY ip is provided by the ISP dynamically. I am using ADSL.

---


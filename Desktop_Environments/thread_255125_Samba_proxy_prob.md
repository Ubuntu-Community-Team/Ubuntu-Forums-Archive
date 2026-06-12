---
title: "Samba proxy prob"
date: 2006-09-11
forum: Desktop Environments
---

### Post by LRC on 2006-09-11
Got Firehol-tinyproxy-Dansguardian withthe assist of tonhou [http://www.ubuntuforums.org/showthread.php?t=207008&highlight=dansguardian+tinyproxy+firehol](http://www.ubuntuforums.org/showthread.php?t=207008&highlight=dansguardian+tinyproxy+firehol). The prob I am facing is that of accessing my M$ box that is connected through a hub. The curious thing is the M$ box can access my Linux box with no problems. The linux box though cannot access the M$ box, cannot even ping it. If I stop Firehol-tinyproxy-Dansguardian I can acces the M$ with no prob. Which leads me to conclude that there is something about the relationship between samba and Firehol that is not in sync. I have added a line that reads server samba accept, but that didn't help much. I have looked all over for help in this regard, but other then describing how to setup stuff (routers, servers etc.) that I have no interest in that is not much out there. And as far as forums are concerned I either get nothing or someone asking me why I set things up the way I did in the first place. I am anoobie to Linux and have no clue as to the opperations of iptables, and from what I have seen in forums as advice how to solve things, it seems there are alot out there with the same prob. Is there a way of instructing iptables to reroute from 192.168.7.151 to 127.0.0.1:3128 as that is how Dansguardian wants the internet to work and therefore the proxies are managed, or as I am using KDE 3.5.4, is there a way of setting the proxy in Kcontrol exempt smb from the list of servers to need the proxy.
Now I must say at this time that I am connected to the internet via the hub, so that I am assuming that that the line in Firehol eading iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP
 affects everything going though eth0. The question I do have regarding that is that I have toggled in the proxy section of Kcontrol, use the same proxy server for all protocols, wouldn't that include smb, or is that not counted as a protocol?

---

### Post by LRC on 2006-09-13
Solved thanks to [http://hr.uoregon.edu/davidrl/samba.html](http://hr.uoregon.edu/davidrl/samba.html). Fixed iptables and samba.

---


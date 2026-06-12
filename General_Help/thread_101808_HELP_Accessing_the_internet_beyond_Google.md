---
title: "HELP: Accessing the internet beyond Google"
date: 2005-12-10
forum: General Help
---

### Post by arzdb on 2005-12-10
I just did a fresh install of Ubuntu on an old desktop machine. It all appears to be working well, except for the internet/network.

I have a network setup where my Ubuntu machine connects directly to a hub with a few other computers also connected to the hub. I can get to google from firefox, but that's about it (I can search, get google images, news, froogle, etc). The other machines (windows) all run fine. It is possible that the hub port that I'm using for this desktop might be slightly broken, but assuming that isn't true, is there anything I can change in Ubuntu?

Note that when I try to go to Yahoo, or these forums for example, it just sits there trying to connect and eventually fails.

---

### Post by teaker1s on 2005-12-10
could be a dns problem find out your isp dns ip set ubuntu up with a static ip and dns ip of your isp. I've had some auto discover problems with ubuntu

---

### Post by arzdb on 2005-12-10
Setting all of that information didn't help, just enabling auto-DHCP works just as well.

It's a wierd problem. I'm not sure if the network card might have problems itself considering I haven't used the computer in a while but I figure that if it can see google and a couple of other really low bandwidth sites then it likely is fine and it's software/hub related.

I did some random search on google and got to a personal.psu.edu website with video, I downloaded one and got like 1300 kb/s speed. Might there be some sort of firewall? (I'm fairly new to linux, but I know a decent amount)

---

### Post by WanderingStar on 2005-12-10
Where are you getting the IP from?  Is it your ISP, A router (not a hub), or a Windows box?  What happens when you ping (ping -c 4 [www.yahoo.com](www.yahoo.com) in a terminal)?  Does it resolve, or die before that?  What is the output of ifconfig for eth0?  What happens if you plug into a different port?  

Or maby I'm misunderstanding the problem ;)

Jeff

---

### Post by arzdb on 2005-12-10
I made up an IP address to assign to it and got the DNS/Gateway info from another computer connected to a different port on the hub. The IP is just a normal network one like 192.168.0.62.

The ping to yahoo seemed to work fine. Here's the final output:
4 transmitted, 4 received, 0% loss, time 3002ms, rtt min/avg/max/mdev = 21.332/24.896/26.854/2.206 ms

The ifconfig looks like it has all of the right info with my ip, mac address, subnet, and here's some info that might be beyond me:
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric: 1
RX packets: 74, 0 for errors, dropped, overruns, frame
TX packets: 100, 0 for errors, dropped, overruns, carrier, collisions:3 txqueuelen:1000
RX bytes: 20238 (19.7 KiB) TX bytes: 13681 (13.3 KiB)
Interrupt: 11 Base address 0xec80

I also tried a different port in the hub and it didn't make any difference.

---

### Post by teaker1s on 2005-12-10
find out the ip of a website and type it if it loads then its DNS

---

### Post by arzdb on 2005-12-10
I tried to get the IP for a couple sites and it didn't help.

yahoo.com (216.109.112.135), just eventually timed out
espn.com (199.181.132.250), it did figure out that it redirects to go.com
ubuntuforums.org (64.21.33.9), just eventually timed out
digg.com (64.191.203.30), figured out it was diggtheblog.blogspot.com, not quite sure but close enough

---

### Post by teaker1s on 2005-12-10
wierd, your not being blocked from certain ip related functions on the network by the router? I can't get my head round how you get google but not yahoo
you could install guarddog to easily reset ubuntu ip tables(firewall) see if that helps

---

### Post by arzdb on 2005-12-10
I don't believe so. 

At this point, unless there is something specific to linux's networking, I think it's probably hardware related considering the other computers on my network don't have any problems.

---

### Post by arzdb on 2005-12-10
Well it can't be a hub problem, I took out a cord from one of those computers and put it into this one and still the same problem (I would have done it earlier but it wasn't easy because part of the hub is in a hard to reach area). So it appears do be a network card or some wierd software problem.

Thanks for the help so far by the way.

EDIT:

I plugged in the desktop into my laptop which uses a bridged network connection (wireless card from my router instead of going through the hub). It now works perfectly. What the heck does this mean, considering other connections on the hub work fine?

---

### Post by _bacon_ on 2005-12-10
Did you install firestarter?

---

### Post by arzdb on 2005-12-11
I haven't installed it, should I?

---


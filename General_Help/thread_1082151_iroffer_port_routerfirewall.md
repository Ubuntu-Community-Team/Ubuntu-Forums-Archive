---
title: "iroffer port router/firewall"
date: 2009-02-27
forum: General Help
---

### Post by Gosujii-sama on 2009-02-27
While using iroffer I noticed that the firewall on ubuntu hardy either by my fault or it's not there doesn't do port ranges? Far as I see it only does spicific ports. What I want to do is setup the package IROffer to work on port 1035 spicifically and not a range but the config of said program says it works in range from specifyed if i put in 1035 it will work 1035-1135 in which case I'm back to my firewall issue. Using a linksys router so I have all the port forwarding correct on there how can I set the firewall up with iroffer to work off a spicific port and not range? If possible. 

Details:
Linksys Router: BEFSR41
Ubuntu Hardy: 8.04
Firewall data current: 

Construct@Diabolic:~$ sudo ufw status
 
Firewall loaded

To                         Action  From
--                         ------  ----
6112:tcp                   ALLOW   Anywhere (WarIII)
6112:udp                   ALLOW   Anywhere
1035:tcp                   ALLOW   Anywhere (Wanted iroffer port)
1035:udp                   ALLOW   Anywhere

Any help you guys can give or point me to a thread somewhere that has more data on the port issue I may be having would be much obliged since after searching the forum turns up nothing on iroffer spicifically for this area.

---

### Post by Gosujii-sama on 2009-02-27
Basically just give me a run down on setup for iroffer.
Anyone thats set it up already since the FAQ and Documentation neither fixed the issues I'm having.
The dcc refuses to send even using the "fix" patch file dynip.sh setting router to all ports forward iroffer 1-65535 to my address I KNOW its the ubuntu firewall now and I need to know how to set it to be fixed for this program.

---

### Post by Gosujii-sama on 2009-03-02
Real lack of help on this one ^_^
On my own I've tried the following:
router: iroffer 1-65535 both (my ip) enable
ufw: manually typed sudo ufw allow 1025-1125
iroffer config: tcprangestart 1025
loaded dynip.sh with iroffer.conf

With all of these done it still refuses to connect or function on my ubuntu hardy 8.04 suggestions? ideas? someone out there must know.

---

### Post by brian_p on 2009-03-02
> **Gosujii-sama said:**
> 

ufw: manually typed sudo ufw allow 1025-1125

The Hardy version of ufw does not do port ranges.

> With all of these done it still refuses to connect or function on my ubuntu hardy 8.04 suggestions? ideas? someone out there must know.

Return iptables to its default state of allowing everything. That will eliminate ufw as a cause of your problem. Why do you think you need ufw anyway?

---

### Post by Gosujii-sama on 2009-03-05
The iptables are set to default with policy allow. The issue is the router which is a BEFSR41 v4.3 I've gone over the issue with the tech support and after alot of work theres still no solution the router continues to block the port range. Without the router hooked up it works fine.
Current router settings:
Static ip: 192.168.2.10
Router ip: 192.168.2.1
WAN: all disabled
mac address is enabled and used
App & Gaming Port Forward: 1025-1125 BOTH tpc/udp 192.168.2.10 Enabled
firmware 2.00.4

Is it possible that ubuntu isn't working with my router properly? Tech for linksys suggested this was the case as their router doesn't work fully with some linux systems. If not that what setting am I missing to make this work properly with iroffer? It's not my default firewall as I've checked by disconnecting the router and transfers work fine so it's definitely the router itself. Tech support for linksys is at wits end with this issue and I'm getting there. Any other suggestions how to get the router to work the way I want it too?

---


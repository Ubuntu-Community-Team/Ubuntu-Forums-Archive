---
title: "need help for a wireless script"
date: 2006-06-02
forum: Desktop Environments
---

### Post by zupermanz on 2006-06-02
I have a wireless ad-hoc network at home and i like to make a scripto to connect my laptop (amilo m 7400) to the network. 
 i do 
sudo iwconfig eth1 essid asirmato mode ad-hoc channel 1 key s:trewq
but im still not able to get to internet.
When i try the same from system settings>>>>>>>> network>>>>>>>>connections>>>>>>>>wireless n>>>>>>activate conf 4 it works!
Anyone knows why?
My wifi is on eth1 , the essid is asirmato and the pass is trewq, channel is 1

Any ideas?
I use kubuntu

---

### Post by zupermanz on 2006-06-02
I think the problem is that i cant get an ip with this script.


EDIT: dhcpcd eth1 did the trick

---

### Post by IndigoMontoya on 2006-06-02
I may be wrong, but I use dhclient3 eth1 - I think it is better.

---


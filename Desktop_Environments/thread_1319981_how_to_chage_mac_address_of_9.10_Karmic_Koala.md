---
title: "how to chage mac address of 9.10 Karmic Koala"
date: 2009-11-08
forum: Desktop Environments
---

### Post by calamus300 on 2009-11-08
[SIZE="3"]hi there 
i tried to change the mac address of ubuntu 9.10 Karmic Koala
but auto ethernet(default) is set every time
i tried /etc/network/interfaces but every time failed
ifconfig eth0 hw ether .......    also failed
tried scripts also failed
any help to change mac address or
disable wired auto ethernet network[/SIZE]

---

### Post by blacksm1th on 2009-11-08
What you did in interfaces file? I use the change mac address tweak. This lines are from my interfaces file:
```
auto eth0
iface eth0 inet dhcp
hwaddress ether 00:13:8F:4F:6B:D8
```

---

### Post by calamus300 on 2009-11-09
thanks blacksm1th for response and reply
but i tried as your code
first there were code:
..................................................
[COLOR="DarkRed"]auto eth0
iface l0 inet loopback
hwaddress ether 00:1[/COLOR]:....( mac adress i changed)
..................................................
then i chancged like u with my mac adress 
but still take the same mac of the device
by the way i'm using vmware and i wanna change vm mac to accept net
from ubuntu as i have internet restriction here i can use only one device to enter the net

---

### Post by umar_zulfiqar on 2010-01-18
hi i am new to ubuntu how i change mac address
the above method is not work for me
i am using ubuntu 9.10
and my interfaces look like this


auto lo
iface lo inet loopback

i have two lan card on my computer for example eth0 and eth1
i want to change eth1 mac address any help>>>>>>>>>?

---

### Post by Piotr.Sniady on 2010-03-29
How about right-clicking on the icon of network manager and then "Edit connections"?

---

### Post by Zane267 on 2010-04-26
I tried left click and edit connections but that did not work for me

---


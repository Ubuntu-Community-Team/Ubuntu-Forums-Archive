---
title: "long period of inactivity during the starting of kubuntu"
date: 2008-07-15
forum: Desktop Environments
---

### Post by opsi on 2008-07-15
Hello all,
Since i had installed KDE, I have some long times during the starting. I'm not an expert in linux (in english as well).
The problem comes just after "configuring network..." The stop during thirty five seconds.
I use "dmesg" command to identify clearly what happened 

```

[   20.804000] Adding 4803392k swap on /dev/disk/by-uuid/43af37c2-97a7-4eaf-afdc-b394e8c42484.  priority:-1 extents:1 across:4803392k
[   20.984000] EXT3 FS on sda1, internal journal
[   21.592000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[   23.000000] NET: Registered protocol family 17
[   59.016000] NET: Registered protocol family 10
[   59.016000] lo: Disabled Privacy Extensions
[   59.016000] ADDRCONF(NETDEV_UP): eth1: link is not ready

```

So we could clearly see that there is a long period without activity between 23 and 59 seconds....
I'm quite sure it is linked with the wifi. What is the protocol family 17 .. ?
If anyone could help me to fix this problem !
Thank you to have read my bad english !
Opsi

---

### Post by benerivo on 2008-07-16
I'm going to guess that it involves the entries listed in /etc/modprobe.d/aliases. These seem to be interent communication protocols. Number 17 is listed as...

alias net-pf-17 af_packet

I don't really know what it does, but I think you can disable these protocols by changing the line to read..

alias net-pf-17 off af_packet

I would try googling for more info, but it also worth pointing out that your log file implies that kde has detected 13 802.11bg channels and 23 802.11a channels. Could that be right, and if so, maybe it just takes kde a long time to 'inspect' them?

---

### Post by opsi on 2008-07-18
Hello,
Thank you for your answer, i will try to test it this evening.
Bye

---

### Post by opsi on 2008-07-19
I have comment this line, but nothing have change .. :-(

---


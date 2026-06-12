---
title: "Strange: Connecting to somebody's router when trying to search 'firefox'"
date: 2008-03-23
forum: Desktop Environments
---

### Post by eizzer on 2008-03-23
I have both Firefox and Epiphany installed and I don't know since when this happen to me but
when I try to search for 'firefox' by typing it on address bar and hit enter both automaticaly
trying to open 82.93.81.75 which is I think someone's router on the Netherland. Take a look at
the screenshot (attached).

There is nothing strange on my /etc/hosts:
```

127.0.0.1       localhost
127.0.1.1       user-desktop

# The following lines are desirable for IPv6 capable hosts
#::1     ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts

```

Any clue? :confused:

---

### Post by eizzer on 2008-03-23
Ok, I think I found what's causing this, but before I'll try to explain my home
network.

Internet --- Modem --- Router --- Computer

My computer is behind wireless router (NAT) which is connected to cable
modem. Dynamic DNS feature on that router is activated using the host/domain
name like **someting.mine.nu** (DynDNS) and I also set the host name of the
router to **something** and domain name to **mine.nu**. Therefore every
time I try to search for 'firefox' both Firefox/Epiphany actually try to to connect
to **firefox.mine.nu (82.93.81.75)**. When there is no host name like the
keyword then either will do the default action, search using Google.

](*,)

---


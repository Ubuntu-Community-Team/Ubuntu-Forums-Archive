---
title: "how to find out ip address"
date: 2009-01-11
forum: General Help
---

### Post by newbux on 2009-01-11
how do i find out my public ip address also just my regular ip adress 


im doing a tutorial that has these instructions

You should be familiar with :

1. Installing from source (don't worry I will walk you through it).

2. Your ip address, both on your private LAN and public IP address

thanks

---

### Post by whoop on 2009-01-11
For public ip address visit [www.probemyports.com](www.probemyports.com) (this page is an online portscanner which will also display your wan ip address.

for lan ip address:
open up a terminal and type: 
```

ip addr show

```

for extra info you can type:
```

ifconfig

```

It could be that both ip addresses are the same (this is the case with a direct connection, when you are not using a router and have no private network). 
In that case both are yout wan ip address

---

### Post by newbux on 2009-01-11
thanks for the help

---

### Post by chex_m8 on 2009-01-11
Your WAN ip address can also be found by checking your routers web based settings page. find out what you routers ip address is and input into your web browser. routers ip address is usually the default gateway.

---

### Post by tuxxy on 2009-01-11
> **whoop said:**
> For public ip address visit [www.probemyports.com]("http://www.probemyports.com") (this page is an online portscanner which will also display your wan ip address.

for lan ip address:
open up a terminal and type: 
```

ip addr show

```for extra info you can type:
```

ifconfig

```It could be that both ip addresses are the same (this is the case with a direct connection, when you are not using a router and have no private network). 
In that case both are yout wan ip address

This will not acquire his external IP, his inet addr: is his network IP address.

[http://ubuntuforums.org/showthread.php?p=6537249#post6537249](http://ubuntuforums.org/showthread.php?p=6537249#post6537249)

---

### Post by andresmh on 2009-01-11
There is also Giplet, a Gnome applet that checks your public IP address against an external site. This is useful when you want to know how the outside world sees you.

---

### Post by L14UX_1NS1D3 on 2009-01-11
You could also do a quick google search to whatismyip.com. Sorta useless but you could open up links terminal web browser have your ip right in terminal.  One could also go on to extending this function and script a query of the IP with links or wget. Just an idea... ):P

---


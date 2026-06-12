---
title: "Problems with my Ubuntu not getting an IP before login"
date: 2009-03-23
forum: General Help
---

### Post by Deathray on 2009-03-23
First, I uninstalled the ubuntu network manager. Then I configured a static IP and dns and confirmed everything was working by visiting google and pinging the machine from another. Then I was happy with my configuration and disabled the GDM so when I turn on my ubuntu, I just get a black screen prompting for a login - exactly the way I want. Now for some reason I can not ping the server when it turns on, how is that and how do I fix it??
I just tried logging in and typing ifconfig and it doesent even show eth0! Do I have to make a script which does:
```
ifconfig eth0 192.168.1.250
route add default gw 192.168.1.1
echo "nameserver xxx.xxx.xxx.xxx" >> /etc/resolv.conf
ifconfig eth0 up
```? If so how do i make it get launched at boot but BEFORE logging in? (I am planning on running an SSH server)

---

### Post by Deathray on 2009-03-23
Okay I successfully created a way of fixing my problem but not sure it is the proper way of doing things in Linux. Here is what I did. I made this script:
```

ifconfig eth0 down
ifconfig eth0 192.168.1.250 netmask 255.255.255.0
route add default gw 192.168.1.1
rm /etc/resolv.conf
echo "nameserver 208.67.222.222\nnameserver 208.67.220.220" >> /etc/resolv.conf
ifconfig eth0 up

```
, put it in /etc/init.d/ip.sh, made it executable and issued the command: update-rc.d ip.sh default
Is that the correct way of fixing my problem?

---

### Post by dcstar on 2009-03-24
> **Deathray said:**
> Okay I successfully created a way of fixing my problem but not sure it is the proper way of doing things in Linux. Here is what I did. I made this script:
```

ifconfig eth0 down
ifconfig eth0 192.168.1.250 netmask 255.255.255.0
route add default gw 192.168.1.1
rm /etc/resolv.conf
echo "nameserver 208.67.222.222\nnameserver 208.67.220.220" >> /etc/resolv.conf
ifconfig eth0 up

```
, put it in /etc/init.d/ip.sh, made it executable and issued the command: update-rc.d ip.sh default
Is that the correct way of fixing my problem?

I would have thought just having this in /etc/network/interfaces would do the job:
```
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.1.250
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0
```

And this in /etc/resolv.conf:
```
nameserver 208.67.222.222
nameserver 208.67.220.220
```

---

### Post by Deathray on 2009-03-24
Aha okay! Never new about that configuration file, thanks I'll go ahead and fix it to the proper way.

---


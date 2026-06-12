---
title: "Internet Connection Sharing trouble..."
date: 2006-06-01
forum: Desktop Environments
---

### Post by Toby on 2006-06-01
**Synopsis**
-----
Need to share internet connection from Desktop computer running Ubuntu with laptop running Windows XP SP2. Firewall disabled on laptop. Desktop has two NIC cards, connects to laptop via crossover cable. eth1 is connecting to my router, which connects to my cable modem. eth0 connects to my laptop the crossover cable. My desktop computer can ping my laptop, and vice-versa. I've got Firestarter installed on my desktop, and I have the ICS checkbox enabled for eth0. Using static IPs all around. Allowing all inbound connections in Firestarter for my laptop's IP.  Laptop is still unable to access the internet. I can't plug the laptop directly into the router, as I don't have another giant cable. (It's quite a long way from the router to the basement.) Been trying various solutions from the forum, and sifting through the wiki / google groups. No luck yet.

_Desktop - eth1 (Internet)_
IP: 192.168.1.200
Subnet Mask: 255.255.255.0
Gateway: 192.168.1.1

_Desktop - eth0 (Connects to Laptop)_
IP: 192.168.0.1
Subnet Mask: 255.255.255.0
Gateway: Blank

_Laptop - LAN connection (Connects to Desktop)_
IP: 192.168.0.2
Subnet Mask: 255.255.255.0
Gateway: 192.168.0.1

**The slightly longer story**
-----
I'm not exactly pleased with myself that my first post to the forums is a support request, especially since it seems to me like this would be a fairly well documented subject.
I've been scouring the forums, the wiki, and google groups trying to get things running on my own, but I've met with very limited success.
Here's the gist of what I've done, and where I am now:

Did a fresh install of Dapper today, and so far, everything has worked beautifully.
I'm happily chatting with my WarCrack guildies on Skype, GAIM is up and running, and I'm getting ready to import my (quite sizable) music library into Banshee...
I was able to install all of this stuff, because I stole my extra-long ethernet cable that was connecting my laptop to the router, and plugged it into my desktop (which now runs Ubuntu again. Hoorah!). My wireless signal is far too weak to be of any practical use, so I've had to choose which computer I wanted connected at the time. (It's always been my laptop, which is basically my workhorse. Desktop is mainly for movies, music, games and such.)

Any help or suggestions would be appreciated.
I'll continue searching in the meantime.
Thanks in advance!

---

### Post by jdbartlett on 2006-06-01
I think I may have a similar problem. I just now installed Ubuntu Dapper. At first, I was directly connected to the cable modem with a line. When I wasn't able to do anything online, I tried disabling eth0 and enabling ath0, connecting to my wireless router. From the wireless router, I'm able to make a connection anywhere within my network (brings up Apache pages, able to access the router admin, etc.) but I'm still not able to get online. All my other computers (PC, Mac) can get online fine. Any ideas, anyone? Thanks.

---

### Post by jdbartlett on 2006-06-01
Toby, (and anyone else having problems with their internet connection), this thread may help:

[http://www.ubuntuforums.org/showthread.php?t=182618&highlight=%22network+unreachable%22](http://www.ubuntuforums.org/showthread.php?t=182618&highlight=%22network+unreachable%22)

Especially Sgood1971's comment, which led me to try this:

```
sudo ifdown ath0
sudo ifup ath0
```

After that, hey presto, internet connection. 'ifdown' and 'ifup' are terminal commands to take a network interface down/ bring it back up.

Hope that helps you, Toby. It solved my problem!

---

### Post by Toby on 2006-06-01
Different problem, it looks like. (Though I did try that, just to see if I would get lucky.)
I can connect to the internet just fine on my desktop.
The problem is that I can't connect my laptop to my router, so I have to share my desktop's connection with the laptop.
I can access my laptop's shared documents from my desktop, but it looks like Firestarter isn't properly sharing the internet connection.
It's not throwing any errors, either...

---

### Post by Jason_25 on 2006-06-01
```

sudo nano /etc/sysctl.conf

```
Uncomment IPv4 forwarding, save and close.

```

sudo iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

```

You might need to restart networking or reboot to get the first change to take effect.  Your IP settings look correct but you might need to experiment with the gateway setting on the laptop.

---

### Post by Toby on 2006-06-01
[QUOTE=Jason_25]```

sudo nano /etc/sysctl.conf

```
Uncomment IPv4 forwarding, save and close.

```

sudo iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

```

You might need to restart networking or reboot to get the first change to take effect.  Your IP settings look correct but you might need to experiment with the gateway setting on the laptop.[/QUOTE]

Just made the changes (in vi, not nano. XP) and right after I :wq!'d and pasted that command string in terminal, well, my buddy called my on Skype.
I had been playing WoW earlier, and he missed my call, so he was calling me back to chat. By this point, my mic was unplugged from my desktop, but Skype was running on both computers.

Here's where it gets interesting:
It rang on my desktop, but I didn't get my mic plugged in fast enough. Stopped ringing.
Then my skype on my LAPTOP started ringing. I can't ping google, but I'm talking to a guildie on Skype.

Wiggy.


Update: Added a new DNS server on my laptop (4.2.2.2) and now everything is as it should be! Rock on, Jason_25. You've just saved the day.

Extra Update: Everything works now. Life is good. :D

---

### Post by kblood on 2006-06-05
Hello there,

I seem to be having the same problem, but I am using Firestarter. Skype connects from the Windows machine (connected through Wireless Ad-Hoc).
The wireless connection works, I can brose the Windows shares from my Ubuntu machine (besides Skype being connected, which already proves that).

My machine has a Ethernet connection (eth0), which is my Internet access. Uses DHCP, gateway 192.168.1.1, DNS the same, IP changes sometimes.
Wireless is eth1, local IP 192.168.0.1. The Windows machine is 192.168.0.2, gateway 192.168.0.1, DNS 192.168.0.1.

I have installed Firestarter, activated the Internet Sharing option, and set a rule that allows all traffic from 192.168.0.2.

Any hints?

---

### Post by kblood on 2006-06-05
Ok, forget it, I am so stupid...

I need to set in the Windows machine 192.168.1.1 as DNS. The IP of the DNS of the external network...

Now everything works perfectly.

---


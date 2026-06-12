---
title: "quick network question"
date: 2009-06-14
forum: General Help
---

### Post by uberlube on 2009-06-14
hey guys, 

[INDENT]I have a server running on my home network which ive assigned a static ip. i can connect to this cpu from any other workstation on my internal network. I have a friend thats trying to connect from outside my network but is having trouble. Do i have to assign all the computers on my network static IP's and turn off DHCP completelly for this to work?[/INDENT]

---

### Post by jakupl on 2009-06-14
Are you sure that it is truly static? Is there no router at eg. you isp or something?

---

### Post by CrusaderAD on 2009-06-14
How is he connecting? Some kinda vpn or thru your wan ip via a certain port or something?

---

### Post by uberlube on 2009-06-14
all my cpus at home are behind a router and he is connecting through ssh. He was just able to log in using my IP as opposed to my dyndns address. so that is where the problem lies. any suggestions as to how to get dyn dns to point to that one box?

---

### Post by nandemonai on 2009-06-14
You need to forward a port from your router to the internal IP you want to be accessible from the outside. The default ssh port is 22.

As a side note, routers will NOT forward internal requests to a WAN address that resides on the current local network. For example, trying to connect to your dyndns dynamic domain name (you'll need to edit your hosts file if you wish to do this internally).

The only way to test external access is via a port scanner from a site like 'Shields Up' or have someone you know attempt access.

---

### Post by uberlube on 2009-06-14
so what your saying is, that when i installed my debian server and gave it its name "server1.blahblah.net" i should have given it the dyndns address instead?

---

### Post by theozzlives on 2009-06-14
To setup my web server, I assigned my static IP to my router, went to LAN settings, clicked "use as DHCP", assigned an IP to each of my computers, and forwarded port 80 to my servers internal IP. That's it!

---

### Post by nandemonai on 2009-06-14
> **uberlube said:**
> so what your saying is, that when i installed my debian server and gave it its name "server1.blahblah.net" i should have given it the dyndns address instead?

No. Ok I'll be a little more specific, sorry I'm in a rush ;)

First you need an internal IP suited for your network. Sounds like you know that and have that bit working so I'll skip that. When you say 'gave it a name' I'm assuming you mean hostname which is also fine.

The thing here is that once you're online you have a external IP address accessible from the internet that is assigned by your ISP. You can go to a site like [http://whatismyip.com/](http://whatismyip.com/) to find this out (not that you really need it).

So what dyn does is map that external IP to a dynamic hostname. You have to have some form of a updater to keep this IP valid if your ISP gives you a dynamic external IP, either on the router itself (most newer routers support this) or from a ddns client installed on a local machine.

If however you have a static external IP set by your ISP then initially setting up dyndns should be enough.

Now, as for the host name..

If you take a look at the servers /etc/hosts file you should notice something like this:

```
cat /etc/hosts
```

```
192.168.1.1 hostname.of.server
```

Obviously IP and hostname will vary depending how you have it setup.

This is to map the hostname you've chosen to the local IP of the server.

If you want to access the server internally from local machines via that hostname then you will need to add that same line displayed on the server to the /etc/hosts file on the client machines (c:\Windows\System32\drivers\etc\hosts in Windows machines).

Finally, in order to allow external access to the server you will need to log into your router and setup a port forward (I'm assuming SSH here) of port 22 to Internal server IP.

Essentially what will happen if it's setup correctly is this.

External client enters your dyndns name -> Dyn resolves the host to your external IP -> Packets end up at your router -> Router determines that all traffic to port 22 should be forwarded onto the local IP of your server -> Server responds and lets you log in.

Hope that made more sense ;)

---

### Post by uberlube on 2009-06-14
It sure did. Thanks for taking the time to help guys. appreciate it!

---


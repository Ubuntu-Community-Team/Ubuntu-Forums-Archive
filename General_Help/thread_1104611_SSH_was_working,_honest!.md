---
title: "SSH was working, honest!"
date: 2009-03-23
forum: General Help
---

### Post by lumpyone on 2009-03-23
I have already had SSH setup on my Ubuntu 8.10 at home, allowing me to connect from work.  I typically shut the computer down over the weekend (as I don't use it for anything else) and when I turned it on this morning it seemed to be working as usual.

However, when I got to work and attempted to use PuTTY to connect, I got a Connection Refused error. I got home, checked my settings on my router, in the sshd_config file, and attempted to connect from a machine locally on my LAN and still have been unable to reach the Ubuntu machine. 

I've tried restarting the ssh service.
I pinged the IP address I use to connect to the machine from work and it's showing a good, strong response. I am using DynDNS.com to route to my machine, and have set up port forwarding on my router which still shows the same IP address externally as well as for the machine on the LAN.  I'm at a loss of what else to do/check to resolve the issue. 

The only change over the weekend, I finished building a new game machine, connected it to the network but assigned it a different IP address on the LAN (the one for the Ubuntu machine is reserved for just that machine). 

Any thoughts would be greatly appreciated!1

---

### Post by Xiong Chiamiov on 2009-03-23
From the local computer you were testing with, try sshing to a remote server, then back in.  If you don't have shell access to any other servers, you can find a free one [here](http://www.red-pill.eu/freeunix.shtml) temporarily.

Have you tried connecting to your home's IP address from work, rather than using DynDNS?

---

### Post by lovinglinux on 2009-03-23
This also happens to me when trying to connect to the remote machine from LAN. 

I don't know why it happens or how to fix this. Restarting the ssh server does not help. The only thing that helps is to reboot the remote machine. Since you access it from office, It would be a good idea to test the ssh connection before living home.

I know it's not a solution, but this could avoid a lot of frustration.

---

### Post by lumpyone on 2009-03-23
I had SSH correctly running with Ubuntu 8.10 for the last few months. I shut the system down over the weekend (like I do every weekend) and when I turned it back on, everything seemed fine except I now am unable to connect to that machine remotely.  I can't even connect to it via PuTTY on another machine on my network.  I even tried to connect to localhost on the machine itself and its still refusing the connection.

What I have done:
1. I checked the sshd_config file and all settings are still correct.
2. I restarted the SSH service
3. I checked my router settings, including the port forwarding and ensured the computer was still using the same IP (which is reserved for that machine)
4. I have tried to connect both through the DynDNS host I setup, as well as directly to the IP address. Still get Connection Refused.

I'm at a loss of what to check next and where my error may be. I'm interested in learning more of how this stuff works, so don't hold back. :)

TIA

---

### Post by bodhi.zazen on 2009-03-23
Threads merged. Please do not start multiple threads on the same topic as it causes confusion and duplication of effort.

---

### Post by bodhi.zazen on 2009-03-23
You need to start on the server with 

ssh localhost

If that is working, ssh to the sever from your LAN.

It that is working make sure your public IP address is unchanged.

---

### Post by lumpyone on 2009-03-23
> **bodhi.zazen said:**
> You need to start on the server with 

ssh localhost

If that is working, ssh to the sever from your LAN.

It that is working make sure your public IP address is unchanged.

My apologies on the double post, I thought the first had been removed. 

Okay, Starting with my server, and typing: 'ssh localhost', I get a connection refused because its trying to connect to port 22. I have switched away from port 22 in my sshd_config file and it was working until today. However, to test, I switched back to port 22 and 'ssh localhost' did allow me to connect from the local machine. 

So I then tried from the one on my LAN and now it works.  Why is it that switching the port would cause that? Do I need to pick a different port than the one I was using?

---

### Post by bodhi.zazen on 2009-03-24
Not sure from what you posted.

Go back to the old port and try again. If it fails we need to check your router and did you perhaps install a firewall ?

---

### Post by lumpyone on 2009-03-24
No new firewall installed, just some updates offered through Ubuntu.  

Will be checking router again. I changed nothing on it, however, I'll check again. Thanks for the assistance.

---

### Post by lumpyone on 2009-03-25
An Update:

I switched back to the default port 22 and it was working just fine for the last couple of days. This morning, again, I attempted to connect remotely and my connection was bring refused. 

I even ping'ed the IP address of the server and was getting a 'Requested Timed Out', thought my connection was down. Just checked the connetion at home and its up and running, no problem. Nothing wrong with it, appears nothing was wrong as far a I can tell. 

I could connect from the host machine with 'ssh localhost', but couldn't connect from another machine on my LAN.  I switched the port again, just for the heck of it and now, again, I can connect remote.  

Any thoughts at all on why the machine would be unavailable on a specific port if nothing else has changed? My router was even restarted before I switched the port, and still I couldn't access it from another machine.  I'd hate to have to just go around changing ports every few days. There has to be something I can do!

---

### Post by DGortze380 on 2009-03-25
> **lumpyone said:**
> An Update:

I switched back to the default port 22 and it was working just fine for the last couple of days. This morning, again, I attempted to connect remotely and my connection was bring refused. 

I even ping'ed the IP address of the server and was getting a 'Requested Timed Out', thought my connection was down. Just checked the connetion at home and its up and running, no problem. Nothing wrong with it, appears nothing was wrong as far a I can tell. 

I could connect from the host machine with 'ssh localhost', but couldn't connect from another machine on my LAN.  I switched the port again, just for the heck of it and now, again, I can connect remote.  

Any thoughts at all on why the machine would be unavailable on a specific port if nothing else has changed? My router was even restarted before I switched the port, and still I couldn't access it from another machine.  I'd hate to have to just go around changing ports every few days. There has to be something I can do!

Ok. for trouble shooting purposes, please pick a port, and stay with it.

please post the output of 
```

sudo iptables -L

```

on the local machine try

```

ssh localhost

```

(or if you changed the default port)
(without <>)

```

ssh localhost:<Port Number>

```

on another machine on your LAN, try to connect using your local IP.
example:

```

ssh myUser@192.168.0.2:22

```

post back and we can start to work this out. The trick is to pick a config, stick with it, start local and move out step by step. Next will be router and firewall configs. Then checking your external IP against your dyndns account. Then connecting via dyndns while at home.

---

### Post by lumpyone on 2009-03-26
> **DGortze380 said:**
> Ok. for trouble shooting purposes, please pick a port, and stay with it.

Okay, I can understand that, so to help resolve this should I switch back to the original port which apparently was having issues? As of the moment, all seems to be working okay after I switched away from both the original port and the default (22).

Or will this still point me to the issue, even if a port is currently working and I'm able to ssh to the remote machine?

---

### Post by DGortze380 on 2009-03-26
> **lumpyone said:**
> Okay, I can understand that, so to help resolve this should I switch back to the original port which apparently was having issues? As of the moment, all seems to be working okay after I switched away from both the original port and the default (22).

Or will this still point me to the issue, even if a port is currently working and I'm able to ssh to the remote machine?

Thats up to you. If it's working I'd leave it. If it stops working post back here.

---

### Post by Slim Odds on 2009-03-26
> **lumpyone said:**
> I even ping'ed the IP address of the server and was getting a 'Requested Timed Out', thought my connection was down. Just checked the connetion at home and its up and running, no problem. Nothing wrong with it, appears nothing was wrong as far a I can tell.

Unless you have your router set up to respond to pings, it won't.
The default for most home DSL/Cable routers is **not** to respond to ping requests. You have to explicitly enable that.

> I could connect from the host machine with 'ssh localhost', but couldn't connect from another machine on my LAN.  I switched the port again, just for the heck of it and now, again, I can connect remote.  

Any thoughts at all on why the machine would be unavailable on a specific port if nothing else has changed? My router was even restarted before I switched the port, and still I couldn't access it from another machine.  I'd hate to have to just go around changing ports every few days. There has to be something I can do!Is your machine using a static IP address on your LAN. It should be.
It's got to be some strange configuration problem. I do this on one of my machines and it works fine all of the time.

---

### Post by lumpyone on 2009-03-26
> **Slim Odds said:**
> Unless you have your router set up to respond to pings, it won't.
The default for most home DSL/Cable routers is **not** to respond to ping requests. You have to explicitly enable that.

Okay, I hadn't seen a setting specifically for turning on/off allowing pings, but that does make sense and I'll try to look further into that today.

> **Slim Odds said:**
> Is your machine using a static IP address on your LAN. It should be.
It's got to be some strange configuration problem. I do this on one of my machines and it works fine all of the time.

The host machine does have a dedicated IP address on the router, I had to do that to ensure the port forwarding would always point to the right machine.  However, I have not set any specific settings on the host machine itself in regards to its IP address on the network. 

I'm going to have to go through DGortze380's suggestions on trouble shooting. I got to work again this morning and I'm encountering the same issues even though before I left I checked the machine at home.  ssh localhost worked, as did connecting from a second machine on the LAN. I thought it was going to work well until I got here and tried to connect.  I'm starting to think its got to be something with the router, but I need to go through those steps first.

---

### Post by DGortze380 on 2009-03-26
> **lumpyone said:**
> ssh localhost worked, as did connecting from a second machine on the LAN. I thought it was going to work well until I got here and tried to connect.  I'm starting to think its got to be something with the router, but I need to go through those steps first.

ok...

check your router settings, thoroughly. Ensure you have the correct IP set, check your port forwarding rules, check your built in firewall.

From any machine on your home LAN, go to whatsmyip.com and make note of your external IP. From any machine on your LAN, try to ssh to your external IP. If this fails, you have a problem with your router. If it works, you have a dyndns update issue.

---

### Post by lumpyone on 2009-03-26
> **DGortze380 said:**
> Ok. for trouble shooting purposes, please pick a port, and stay with it.

please post the output of 
```

sudo iptables -L

```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         


> on the local machine try

(or if you changed the default port)
(without <>)

```

ssh localhost:<Port Number>

```

ssh: Could not resolve hostname localhost:<Port Number>: Name or service not known

> 
on another machine on your LAN, try to connect using your local IP.
example:

```

ssh myUser@192.168.0.2:22

```

This allowed me to connect to the machine. 

> From any machine on your home LAN, go to whatsmyip.com and make note of your external IP. From any machine on your LAN, try to ssh to your external IP. If this fails, you have a problem with your router. If it works, you have a dyndns update issue.

I verified my external IP, attempted to ssh from a machine on my LAN. It allowed me to connect.  I attempted from an external source and get the same Connection Refused.

---

### Post by DGortze380 on 2009-03-27
> **lumpyone said:**
> Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         






This allowed me to connect to the machine. 



I verified my external IP, attempted to ssh from a machine on my LAN. It allowed me to connect.  I attempted from an external source and get the same Connection Refused.

It sounds to me like you're having firewall issues.
Check your port forwarding and built-in firewall rules.


Where are you trying to connect from when you're outside the LAN? 

The other (probably more likely option) is that a firewall on that end is blocking your connection. 

You could try setting up ssh and port forwarding on port 443, that typically allows encrypted traffic no matter what network you're on.

---

### Post by lumpyone on 2009-03-27
> **DGortze380 said:**
> Where are you trying to connect from when you're outside the LAN? 

The other (probably more likely option) is that a firewall on that end is blocking your connection. 

You could try setting up ssh and port forwarding on port 443, that typically allows encrypted traffic no matter what network you're on.

I'm attempting to connect from work, and as I mentioned earlier, it seemed to work fine until Monday, then every day after my system all appeared fine, but I was getting refused.  Perhaps it is the firewall at work, as I do know they are a bit paranoid. I'll give 443 a try.

Thanks again for all the help.

---


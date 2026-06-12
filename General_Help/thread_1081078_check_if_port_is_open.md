---
title: "check if port is open"
date: 2009-02-26
forum: General Help
---

### Post by miroslav_karpis on 2009-02-26
Hi,
please can you help me with this? I'm trying to run 2 applications that should connect each other (localhost and 2 ports). Ports are defined correctly but still I'm getting reply that the 2 application are not connected.

1. Is there a way to check if the ports I want to use are blocked/opened?
2. How can I open a port?

many thanks in advance..

---

### Post by mcduck on 2009-02-26
Unless you have installed/configured a firewall yourself then all ports are open.

If you have a firewall, you must have closed the ports yourself. In that case check your firewall configuration.

(Having all ports open is safe as the default Ubuntu install doesn't have any running services that would listen for incoming network connections. Because of this there's no need to use a  firewall close any ports.)

---

### Post by miroslav_karpis on 2009-02-26
I see...

is there some way a listener that I would listen that what is going on on a port?

Like packets received, send,...etc..

---

### Post by miroslav_karpis on 2009-02-26
I have downloaded 'wireshark' and when I run my applications I can see them there with a message **'Destination unreachable (port unreachable)'**

does this mean that the port is closed?

---

### Post by Thanoulis on 2009-02-26
By default, debian-ubuntu uses iptables. That means that you already have firewall. Also, by default all ports are closed.
Try it yourself if you like:
```
sudo apt-get install nmap
```
then:
```
sudo nmap <your ip address>
```
and you'll see if you have any ports opened.
If you want to play more with nmap, type:
```
man nmap
```

---

### Post by miroslav_karpis on 2009-02-26
thnks.----so after one day I figured it out. Of course the problem was in my program:confused: the port was overwritten at the end of build....

anyway wireshark helped!!!:guitar:

---

### Post by mb_webguy on 2009-02-26
> **mcduck said:**
> Unless you have installed/configured a firewall yourself then all ports are open.

If you have a firewall, you must have closed the ports yourself. In that case check your firewall configuration.

(Having all ports open is safe as the default Ubuntu install doesn't have any running services that would listen for incoming network connections. Because of this there's no need to use a  firewall close any ports.)

Sorry to be contrary, McDuck, but that's actually incorrect.

By default, all ports in Ubuntu are *closed*.  A port is *open* if a server is listening on a part, which in a default installation of Ubuntu none are.  A port may be *stealthed* by running a firewall.

Suppose you want to go to a pub, and suppose that to get into a pub, someone has to let you in.  You walk up to one, knock on the door, and no one answers.  This pub is closed.  

So you walk down the street to where you know there's another pub.  But they've hired a bouncer who's not letting people in.  This pub is stealthed.

So you walk down the street a bit further to another pub, knock on the door, and somebody opens the door and lets you in.  This pub is open.

From a security standpoint, there's not much difference between a closed pub/port and a stealthed pub/port.  No one can get in either way.  If you're not running any servers (which, in this analogy, are the drunks that let people into your pub), you don't need a firewall (e.g. a bouncer).

---

### Post by Slim Odds on 2009-02-26
In the original message, he mentioned using localhost. If that is the case, then firewalling is not applicable.

Try:
```
netstat -lutn
``````
man netstat
```for details


P.S. What, exactly, are you trying to do?

---

### Post by mcduck on 2009-02-26
> **mb_webguy said:**
> Sorry to be contrary, McDuck, but that's actually incorrect.

By default, all ports in Ubuntu are *closed*.  A port is *open* if a server is listening on a part, which in a default installation of Ubuntu none are.  A port may be *stealthed* by running a firewall.
Well, in fact they are open, as there's nothing specifically closing them.

"Open" means that when trying to connect to that port the machine responds that yes, there's a computer in this address, and then either allows the connection (if there's anything to connect to on that port) or responds that there is nothing to connect to in this port.

"Closed" means that when trying to connect to that port, the machine responds that yes, there is a computer in this address but connection is not allowed. This is what happens when you have a firewall running.

"Stealthed" means that the computer doesn't respond at all (thus trying to give a message that there wouldn't be a machine on that address at all.) Some firewalls include option for this kind of behaviour, although it doesn't really work as if there really wasn't any machine on that address, the computer trying to connect to it would get a return message telling that such address doesn't exist. So who ever is trying to connect to stealthed machine will know that a machine exists on that address simply because he gets absolutely no response at all. And now he also knows that the machine is trying to hide itself..


edit: since you seem to like pub door analogies, let me put it this way:

1. There's a door, it's not locked and either there's a pub behind the door (running service that listens for incoming connections) or there's absolutely nothing behind the door so you can't enter even when the door itself was open (as in default Ubuntu install)..

2. There's a door, and it's locked. If there's a pub behind the door or not, you can't enter anyway since the door is locked.

3. There's a door that's locked, and painted to look like the surrounding wall to hide the door itself. Now you *really* want to know what's inside, must be interesting since they are trying to hide it so hard.. :D

---

### Post by mb_webguy on 2009-02-26
> **mcduck said:**
> Well, in fact they are open, as there's nothing specifically closing them.

"Open" means that when trying to connect to that port the machine responds that yes, there's a computer in this address, and then either allows the connection (if there's anything to connect to on that port) or responds that there is nothing to connect to in this port.

"Closed" means that when trying to connect to that port, the machine responds that yes, there is a computer in this address but connection is not allowed. This is what happens when you have a firewall running.

"Stealthed" means that the computer doesn't respond at all (thus trying to give a message that there wouldn't be a machine on that address at all.) Some firewalls include option for this kind of behaviour, although it doesn't really work as if there really wasn't any machine on that address, the computer trying to connect to it would get a return message telling that such address doesn't exist. So who ever is trying to connect to stealthed machine will know that a machine exists on that address simply because he gets absolutely no response at all. And now he also knows that the machine is trying to hide itself..

Um... no, that's not correct.  Many people confuse "closed" and "stealthed", but whether a port is open or closed typically depends upon whether there is a process listening at that port.  A closed port usually has nothing to do with a firewall.  However, a firewall *can* close a port even if there is a process otherwise listening.

If you doubt this, look at your iptable settings.  Iptables is the Linux firewall, for which programs like ufw and Firestarter are just front-ends.  If you run "sudo iptables -L" in a default installation of Ubuntu, you should see the following:```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```Notice that the policy for everything is ACCEPT.  This means that iptables isn't blocking any ports -- so if what you say is true, then all ports should be open, and none should be either closed or stealthed.   

Now run nmap on your system.  (If you don't want to install it, you can do an [online scan]("http://nmap-online.com/").)  You won't see any open ports, and all of the ports you see are closed.  In other words, the ports are closed not because of the firewall, but because there are no processes listening at those ports.

If the policy in iptables for a port was DROP, then the port would be stealthed and wouldn't show up on an nmap scan.  If the iptables policy was REJECT, then the ports would report as closed, but a closed port usually has nothing to do with a firewall.

---

### Post by Slim Odds on 2009-02-26
You two should start a separate post.....

---


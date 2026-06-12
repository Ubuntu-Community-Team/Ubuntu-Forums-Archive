---
title: "Messed up my IPTABLES"
date: 2009-02-05
forum: General Help
---

### Post by mojo_man on 2009-02-05
Hi,

I messed up my IPTABLES by adding/dropping ports so I get this:

ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:6881 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:6881 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:6881 
           tcp  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:5900 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:5900 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:5900 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:6665 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:50938 
DROP       tcp  --  anywhere             anywhere            tcp dpt:6881 
DROP       tcp  --  anywhere             anywhere            tcp dpt:6881 
DROP       tcp  --  anywhere             anywhere            tcp dpt:6881 

How do I remove all the ACCEPT's and DROP's?
Another question when I open some ports when I use nmap to do a port scan how come it says the only port open is:

Starting Nmap 4.62 ( [http://nmap.org](http://nmap.org) ) at 2009-02-05 23:54 EST
Initiating Connect Scan at 23:54
Scanning localhost (127.0.0.1) [1715 ports]
Discovered open port 631/tcp on 127.0.0.1
Completed Connect Scan at 23:54, 0.03s elapsed (1715 total ports)
Host localhost (127.0.0.1) appears to be up ... good.
Interesting ports on localhost (127.0.0.1):
Not shown: 1714 closed ports
PORT    STATE SERVICE
631/tcp open  ipp

Read data files from: /usr/share/nmap
Nmap done: 1 IP address (1 host up) scanned in 0.067 seconds
           Raw packets sent: 0 (0B) | Rcvd:

---

### Post by jerome1232 on 2009-02-06
> **mojo_man said:**
> Hi,

I messed up my IPTABLES by adding/dropping ports so I get this:

ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:6881 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:6881 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:6881 
           tcp  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:5900 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:5900 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:5900 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:6665 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:50938 
DROP       tcp  --  anywhere             anywhere            tcp dpt:6881 
DROP       tcp  --  anywhere             anywhere            tcp dpt:6881 
DROP       tcp  --  anywhere             anywhere            tcp dpt:6881 

How do I remove all the ACCEPT's and DROP's?

You can flush out all of iptables rules and start over by flushing the rules
```
sudo iptables -F
```

> **mojo_man said:**
> 
Another question when I open some ports when I use nmap to do a port scan how come it says the only port open is:

Starting Nmap 4.62 ( [http://nmap.org](http://nmap.org) ) at 2009-02-05 23:54 EST
Initiating Connect Scan at 23:54
Scanning localhost (127.0.0.1) [1715 ports]
Discovered open port 631/tcp on 127.0.0.1
Completed Connect Scan at 23:54, 0.03s elapsed (1715 total ports)
Host localhost (127.0.0.1) appears to be up ... good.
Interesting ports on localhost (127.0.0.1):
Not shown: 1714 closed ports
PORT    STATE SERVICE
631/tcp open  ipp

Read data files from: /usr/share/nmap
Nmap done: 1 IP address (1 host up) scanned in 0.067 seconds
           Raw packets sent: 0 (0B) | Rcvd:

That's because your not actually opening the ports, your just telling iptables to not block them. In order for a port to be opened a program has to be listening for connections, on a default install of Ubuntu the only service really listening is cupsd (your printer service) and it only listens to localhost meaning no other computer can connect to the service.

For an accurate picture run nmap from another computer, the loop back interface (that's what's getting scanned when you scan localhost) doesn't get filtered by iptables. Even if you set iptables to allow everything you will have zero ports open from another computers point of view.

---

### Post by mojo_man on 2009-02-06
What is a loop back interface and what do you mean by "doesn't get filtered by iptables. "

---

### Post by jerome1232 on 2009-02-06
if you look at your nmap output, when you scan localhost it scans 127.0.0.1, this is a special ip address that's called the loopback interface, it just means that your machine can talk to itself over it.

iptables isn't going to have anything to do with that interface since it's always going to be used by your own computer, blocking anything on that particular interface would cause alot of programs to stop working anyways.

So if you have a port open on localhost then it's only listening to connections from your own computer not other computers. Which is why you need to scan from another computer to see what ports are open to the world.

---

### Post by mojo_man on 2009-02-06
> **jerome1232 said:**
> if you look at your nmap output, when you scan localhost it scans 127.0.0.1, this is a special ip address that's called the loopback interface, it just means that your machine can talk to itself over it.

iptables isn't going to have anything to do with that interface since it's always going to be used by your own computer, blocking anything on that particular interface would cause alot of programs to stop working anyways.

So if you have a port open on localhost then it's only listening to connections from your own computer not other computers. Which is why you need to scan from another computer to see what ports are open to the world.

I do not follow you 100%  What happens when I scan ports on my computer FROM my own computer? What happens when I scan ports on my computer FROM another machine?

---


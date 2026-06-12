---
title: "ubuntu telnet problems"
date: 2005-12-23
forum: General Help
---

### Post by zomgie on 2005-12-23
Hey guys.

Im trying to play around with telnet / ssh, however when I try to telnet my other compy (also running ubuntu) I get a connection refused error.

so comp a wants to telnet comp b, no dice.

I tried googling for answers, and from this gathered I had to edit computer b's /etc/hosts.allow file and added ALL: 192.168.x.x (compy a)

however still no joy.

can someone help this diry, dirty newby? =) 

cheers, and merry xmas

---

### Post by schilcha on 2005-12-23
Did you make sure, your telnet server (I guess it's inetd) is running?

If I try to telnet to my machine, I get:
> 
$ telnet localhost
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

I definitely have no telnet server / inetd installed.

To make sure, execute "netstat -ltn" and see if there's an application listening on port 23 -- telnet default port.

Good Luck"

---

### Post by darth_vector on 2005-12-23
to start with, telnet is insecure. never use it outside your own network and dont allow anyone from the outside telnet into your network.

that said, have you set up a telnet or ssh server on any of the machines? to do so is really simple - let us stick to ssh for good practice:

```
sudo apt-get install ssh
```

it will work out of the box. just

ssh ip_of_destination -lusername

where the l is a lowercase L

---

### Post by linuxbtdsc on 2005-12-23
What's the operating system of the box you are trying to telnet into? If it's a Windows XP with SP2 then you need to ensure you have the built in firewall turned off or open the port so you can telnet.

-linuxbtdsc

---

### Post by zomgie on 2005-12-23
thanks so much for your input guys; theres so much that they dont seem to include in these "beginning unix" books >_<.

darth_vector's solution worked, now that I have installed ssh on both compys I can ssh across.  awesome!  thanks bro.

interestingly, both are using ubuntu 5.10, both are relatively fresh installations.. comp a can ssh to comp b.. but when comp b tries to ssh to comp a.. it just pauses and nothing ever happens. odd.

no matter. it works on the computer that matters!  :D

---

### Post by mscman on 2006-01-15
[QUOTE=zomgie]

interestingly, both are using ubuntu 5.10, both are relatively fresh installations.. comp a can ssh to comp b.. but when comp b tries to ssh to comp a.. it just pauses and nothing ever happens. odd.

no matter. it works on the computer that matters!  :D[/QUOTE]

is comp a running a firewall, by chance?  if so, the firewall might be rejecting the ssh connection.

---


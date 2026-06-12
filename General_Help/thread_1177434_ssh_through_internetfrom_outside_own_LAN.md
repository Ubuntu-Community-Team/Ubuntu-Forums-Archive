---
title: "ssh through internet/from outside own LAN"
date: 2009-06-03
forum: General Help
---

### Post by Isilion on 2009-06-03
hi. im trying to make my pc able to be remotely runned. i have set a printer and two pc's in a LAN, and a pc can connect to other devices. but what i'm looking for now its connect to any net device from outside my LAN.

                                 
                           wifi modem (89.x.x.x)
                                     |
                                     | connected to pc1 by eth0 and USB
                                     |
        pc2:192.168.0.193 ~ pc1:192.168.0.194 ~ printer:192.168.0.195
       (connected by wifi)                     (smart wireless printer)


i suppose that i must set up static ips for each device. but then how will "ssh user@89.x.x.x" know what device connect to? or it's suppossed to do in other way? thanks

---

### Post by blueridgedog on 2009-06-03
One way of getting at this would be to forward your public IP, port 22 (ssh) in to your Ubuntu system, and once you get an ssh session going on that system, you can hop via ssh from it to others behind your dsl modem.  You will need to bring up the configuration setting for your modem to enter your port forwarding rules on it.

---

### Post by Isilion on 2009-06-03
thanks, i was helped in the irc too and get the same andswer. i did something better, i opened 3 ports (8082.8083,8084) and forwarded each one to a network device. but still not work. 'localhost' work on each pc but [http://89.x.x.x:8083](http://89.x.x.x:8083) (ie) dont work. i think each device must listen to a port or i m wrong? what is failing?

---

### Post by blueridgedog on 2009-06-03
If you are forwarding port 8082 to port 22 on one machine, then port 8083 to port 22 on another and finally port 8084 to port 22 on another, you should then be able to enter ```
ssh -p 8082 xxx.xxx.xxx.xxx
``` from a system outside your lan and have it connect (assuming you have the correct external IP address that your ISP has given your device).  If it fails, then perhaps your ISP is blocking the connection or you do not have the routing setup.

I am not certain what you mean with http....

Can you ssh to the three systems on your lan from each other system?

---

### Post by Isilion on 2009-06-04
these are the 3 forwards i did:

No.   	 IP externa   	 IP interna   	 Lím. inf. rango   	 Lím. sup. rango   	  	 

11 	89.7.172.18 	192.168.0.193 	8083 	8083 	
	
12 	89.7.172.18 	192.168.0.192 	8082 	8082 	
	
13 	89.7.172.18 	192.168.0.194 	8084 	8084

i want to use the routing for general purpose (making a home server, and manipulate it both from inside and outside own LAN). how i know it is done correctly? there shouldnt be something like 192.168.0.19x:y to tell the port in each redirection? and that port must be open too. how i open it¿? i was messing with iptables but i dunno if the rule must be OUTPUT, INPUT, FORWARD or what. packets must sent in both directions. please tell me a command line like:

iptables -A OUTPUT -p udp --sport 808x -j ACCEPT && /
iptables -A OUTPUT -p tcp --sport 808x -j ACCEPT 

that is what i did till the moment.

---

### Post by Isilion on 2009-06-04
i called my ISP and made sure forwards are done. they told me that i must listen 89.x.x.x:808y on each machine. please can tell me anyone how?
is using iptables?

---

### Post by blueridgedog on 2009-06-04
> **Isilion said:**
> these are the 3 forwards i did:

No.   	 IP externa   	 IP interna   	 Lím. inf. rango   	 Lím. sup. rango   	  	 

11 	89.7.172.18 	192.168.0.193 	8083 	8083 	
	
12 	89.7.172.18 	192.168.0.192 	8082 	8082 	
	
13 	89.7.172.18 	192.168.0.194 	8084 	8084

i want to use the routing for general purpose (making a home server, and manipulate it both from inside and outside own LAN). how i know it is done correctly? there shouldnt be something like 192.168.0.19x:y to tell the port in each redirection? and that port must be open too. how i open it¿? i was messing with iptables but i dunno if the rule must be OUTPUT, INPUT, FORWARD or what. packets must sent in both directions. please tell me a command line like:

iptables -A OUTPUT -p udp --sport 808x -j ACCEPT && /
iptables -A OUTPUT -p tcp --sport 808x -j ACCEPT 

that is what i did till the moment.

Then you will also need to change the port that sshd listens on on each system.  To do that

```
gksudo gedit /etc/ssh/sshd_config
```

Change the port to the port from 22 to the one you have forwarded.

Restart sshd:

```
sudo /etc/init.d/ssh restart
```

Just to verify again:  Can you currently use ssh internally to each system?

While you are debugging this I recommend that you remove all iptables rules other than a default accept.

---


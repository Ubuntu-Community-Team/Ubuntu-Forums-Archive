---
title: "iptable for webmin port 10000"
date: 2009-06-22
forum: General Help
---

### Post by toik on 2009-06-22
Hello

After setting the iptables, I can't access webmin port 10000 and oracle port 8080 via browser.

What I did was, I wanted to have pptp vpn so I set the D-Link router to have my server exposed to the internet by using DMZ.
When I enable the DMZ all the ports asscessible from LAN were also exposed to the internet.  So I opened port 1723 to be accessible from internet and ones that I need to access applications within LAN such as oracle, SSH and webmin but these ports are accessed only from LAN.  Then closed all the other ports.

I tried to connect oracle by browser [http://server_ip:8080](http://server_ip:8080) from LAN but I can't connect.  Neither webmin [https://server_ip:10000](https://server_ip:10000).
Oracle can be accessed through 1521.

What is the command or setting up to be able to access the webmin and oracle from browser?

The command I used are as follows:
sudo iptables -I INPUT 1 -i lo -j ACCEPT
sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
sudo iptables -A INPUT -i eth1 -p tcp --dport 1723 -j ACCEPT
sudo iptables -A INPUT -i eth1 -p gre -j ACCEPT
sudo iptables -A INPUT -i eth1 -p tcp -m tcp -s 192.168.1.0/24 --dport 1521 -j ACCEPT
sudo iptables -A INPUT -i eth1 -p tcp -m tcp -s 192.168.1.0/24 --dport 22 -j ACCEPT
sudo iptables -A INPUT -i eth1 -p tcp -m tcp -s 192.168.1.0/24 --dport 80 -j ACCEPT
sudo iptables -A INPUT -i eth1 -p tcp -m tcp -s 192.168.1.0/24 --dport 8080 -j ACCEPT
sudo iptables -A INPUT -i eth1 -p tcp -m tcp -s 192.168.1.0/24 --dport 10000 -j ACCEPT
sudo iptables -A INPUT -j DROP

Please someone advise me.

Ubuntu 8.04 Desktop.

---

### Post by The Cog on 2009-06-22
I don't see anything obviously wrong with the iptables rules. Except that I would prefer to see a policy of drop rather than adding a rule to drop at the end (iptables -P INPUT DROP), but that's not your problem.

I suggest you use **iptables -nvL** to see the counters and make sure the rules went in OK. Beyond that, I would install wireshark and use that to watch the packets and see what's really happening on the wire.

---

### Post by toik on 2009-06-23
Thank you for prompt reply.
I checked iptables -nvL and the port 8080 has pkts = 12 and bytes = 600, this means the port is opened, right?  But I can't access [http://server_ip:8080/apex](http://server_ip:8080/apex) from the LAN computer.  It trys to connect but in the end there are no error message from browser and go back to the previous web page that I had it opened.  If I flash the iptables it works again...
I don't know what happened but the I can access to webmin through browser from LAN computer. 
The command was same as the first post: sudo iptables -A INPUT -i eth1 -p tcp -m tcp -s 192.168.1.0/24 --dport 10000 -j ACCEPT
But this command doesn't work for oracle port 8080....

---

### Post by The Cog on 2009-06-23
> **toik said:**
> I checked iptables -nvL and the port 8080 has pkts = 12 and bytes = 600, this means the port is opened, right?No. It means that the firewall rules recognised some packets matching that rule. Since it is a -j ACCEPT, those packets would have been allowed through to the computer. It doesn't mean that an application is actually listening on port 8080 though.

Are you flushing the tables each time before running that script? The rules are scanned in order, and any rules added after the -j DROP rule will have no effect because the packets will have already been dropped.

---

### Post by toik on 2009-06-24
I flash the tables and I retype the command to open the required ports when I want to make changes on the tables and I don't add any rules after -j DROP.  All the ports apart from the oracle port 8080 are working fine.
So the port 8080 is opened but application is not listening the port.
I am not sure what I can do from here.
When I flash the table it I can access the oracle via [http://server_ip:8080](http://server_ip:8080).  This means do I need to add something apart from port 8080 or problems with oracle?

What could you think about the possiblity that causing this?

Thank you very much and I appreciate your help.

---

### Post by The Cog on 2009-06-24
Maybe the port on 8080 just redirects to another port whcih you haven't opened. Maybe somethign else. That's why I would install wireshark and find out what's really happening. But if port 8080 is redirecting to another port, that other port might be a dynamic number, which will make your firewalling rather more tricky. You may just have to pass everything from 192.168.1.0/24. 

Maybe try this: turn the firewall off, connect your Oracle client, and use **sudo netstat -pnt** to see which ports are connected.

---

### Post by bodhi.zazen on 2009-06-24
> **The Cog said:**
> I don't see anything obviously wrong with the iptables rules. Except that I would prefer to see a policy of drop rather than adding a rule to drop at the end (iptables -P INPUT DROP), but that's not your problem.

Just to add a dissenting opinion on that ...

You have to be very careful when setting the default policy to DROP.

If you run iptables -F , and the default policy is DROP, the result is lock out.

IMO adding a drop rule at the end of a table is better as to prevent lock out (it is amazing how often people lock themselves out by playing with firewalls, lol).

---

### Post by bodhi.zazen on 2009-06-24
In terms of solving the problem at hand ...

Try running ```
sudo iptables -L -v
```

That will show the numbers of packets processed by each rule and the drop.

My only other thought is that your rules to accept packets specify eth1 , is your traffic on eth0 ?

---

### Post by toik on 2009-06-25
I will install wireshark as you said and will see what is happing there.
Thank you very much!!

---


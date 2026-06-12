---
title: "Monitor SSH Data Transfer"
date: 2009-01-27
forum: General Help
---

### Post by Rezzie on 2009-01-27
Is there any way of monitoring the amount of bandwidth used during an SSH session?

I am interested to see how much traffic I am using tunneling my web browsing through it as a SOCKS proxy, and also to see how much difference adding the -C option can make to some often accessed files.

Also, any help with **[this]("http://ubuntuforums.org/showthread.php?t=1045314")** please?

Thanks in advance.

---

### Post by bodhi.zazen on 2009-01-27
you can monitor your traffic with iptables :

[http://www.linux.com/articles/50649](http://www.linux.com/articles/50649)

I do not know of a gui to set iptables up.

iptables has a steep learning curve and I am working on a how to for iptables, it is not finished yet and I seem to work on it in spurts and bursts but you are welcome to use it if you like (or google iptables)

[http://bodhizazen.net/beginners/Firewall/](http://bodhizazen.net/beginners/Firewall/)

---

### Post by Rezzie on 2009-01-27
Thanks for the links. Would you please be able to offer a simple rule, or sequence of commands, for me to log total incoming/outputing traffic on port 22?

From the links you provided it seems I could check this using **iptables -vL**, though I cannot work out the rule to define what to log:)

---

### Post by bodhi.zazen on 2009-01-27
iptables -A INPUT -p tcp --dport 22 -j LOG --log-prefix 'SSH Traffic IN' --log-level 7
iptables -A INPUT -p tcp --dport 22 -J ACCEPT

iptables -A OUTPUT -p tcp --sport 22 -j LOG --log-prefix 'SSH Traffic OUT' --log-level 7
iptables -A OUTPUT -p tcp --sport 22 -j ACCEPT

Proceed those commands with sudo.

Note those rules will log permit all traffic on port 22 and you may wish to modify or add blocking rules prior to them ;)

this will also fill your logs (depending on how much traffic you have)

logs are to /var/logs/messages, although you can change that ;)

[http://www.cyberciti.biz/tips/force-iptables-to-log-messages-to-a-different-log-file.html](http://www.cyberciti.biz/tips/force-iptables-to-log-messages-to-a-different-log-file.html)

---

### Post by Rezzie on 2009-01-27
Hmm, I ran those commands and ran */etc/init.d/sysklogd restart* (was that necessary?) but running *tail -f /var/log/messages* shows that no SSH messages are being added.

There were also a couple of typos in the 2nd command, but I corrected those before running it. Any ideas?

Thanks again for the help.

---

### Post by bodhi.zazen on 2009-01-27
although my typing is not the best, what typos ?

Look at (or post) iptables -L -v

order of the rules count.

Is there any ssh traffic ?

---

### Post by Rezzie on 2009-01-28
*iptab**el**s -A INPUT -p tcp --dport 22 -**J** ACCEPT*
should be:
*iptables -A INPUT -p tcp --dport 22 -j ACCEPT*

Yes, there was SSH traffic - I ran the commands and then opened a terminal, started a new SSH session and used it for a bit, but there was no mention of it in the logs.

I'll post the output of *iptables -vL* when I get back (away from the machine in question atm).

Thanks again for the helpful replies.

---

### Post by Rezzie on 2009-01-28
```
Chain INPUT (policy DROP 8 packets, 12000 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       192.168.0.1          0.0.0.0/0           tcp flags:!0x17/0x02 
    3  1147 ACCEPT     udp  --  *      *       192.168.0.1          0.0.0.0/0           
  878  148K ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
    0     0 DROP       all  --  eth0   *       0.0.0.0/0            255.255.255.255     
    0     0 DROP       all  --  *      *       0.0.0.0/0            192.168.0.255       
    0     0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
    1    28 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
    0     0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    0     0 LSI        all  -f  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
28041   42M INBOUND    all  --  eth0   *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:22 LOG flags 0 level 7 prefix `SSH IN' 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:22 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 

Chain OUTPUT (policy DROP 1 packets, 40 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       192.168.0.10         192.168.0.1         tcp dpt:53 
    3   188 ACCEPT     udp  --  *      *       192.168.0.10         192.168.0.1         udp dpt:53 
  878  148K ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
    0     0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
15137  621K OUTBOUND   all  --  *      eth0    0.0.0.0/0            0.0.0.0/0           
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output' 
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spt:22 LOG flags 0 level 7 prefix `SSH OUT' 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spt:22 

Chain INBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination         
28041   42M ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 LSI        all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain LSI (2 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 
    0     0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LSO (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound ' 
    0     0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
15132  621K ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    5   220 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           
```

Is the output. I've never manually added anything to it, and it seems quite busy - is it all necessary? Can I remove/simplify any of it?

---


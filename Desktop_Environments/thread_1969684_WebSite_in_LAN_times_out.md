---
title: "WebSite in LAN times out"
date: 2012-04-30
forum: Desktop Environments
---

### Post by richardhwinter on 2012-04-30
It's my first post here - please be patient.
I have an issue I'm trying to solve for months now and never got it solved. There are many similar posts related but none worked for me.
I'm running Lucid and have Apache2 installed and running fine on my PC (64bit).
After using it first as test server I have now developed a private application and would like to share it with the other machines on the network.
I have set up virtual host and put them in the hosts file on the remote machine.
The domain pings fine, but from the browser I get a timed out connection.
tcpdump -i any -vvv port 80 shows that the packets are received but I see only session start flags.
Example:
```
17:33:42.563131 IP (tos 0x0, ttl 64, id 49530, offset 0, flags [DF], proto TCP (6), length 60)
    192.168.1.4.40669 > 192.168.1.2.www: Flags [S], cksum 0x6606 (correct), seq 2212091403, win 14600, options [mss 1460,sackOK,TS val 8465416 ecr 0,nop,wscale 6], length 0
17:34:06.339966 IP (tos 0x0, ttl 64, id 8206, offset 0, flags [DF], proto TCP (6), length 60)
    192.168.1.4.40668 > 192.168.1.2.www: Flags [S], cksum 0x1802 (correct), seq 1501312822, win 14600, options [mss 1460,sackOK,TS val 8471360 ecr 0,nop,wscale 6], length 0
17:34:06.596088 IP (tos 0x0, ttl 64, id 49531, offset 0, flags [DF], proto TCP (6), length 60)
    192.168.1.4.40669 > 192.168.1.2.www: Flags [S], cksum 0x4e8e (correct), seq 2212091403, win 14600, options [mss 1460,sackOK,TS val 8471424 ecr 0,nop,wscale 6], length 0
^C
10 packets captured
10 packets received by filter
0 packets dropped by kernel
```

I guess it has to do with iptables setup. I opened port 80:
```
richard@richard-laptop:~$ sudo ufw status
Status: active

Zu                         Aktion      Von
--                         ------      ---
22/tcp                     ALLOW       192.168.0.0/24
80/tcp                     ALLOW       Anywhere

```
Does't seem to help.

Here the netstat output:
```
richard@richard-laptop:~$ sudo netstat -tulpen | grep apache
[sudo] password for richard: 
tcp6       0      0 :::80                   :::*                    LISTEN      0          6235        1495/apache2    

```

Funny thing is, it worked before I switched tu Lucid. 
After trying so many things I'm running out of ideas and courage.

Your help is appreciated.

Thanks

Richard

---

### Post by dchrono on 2012-04-30
when you say the **domain pings fine**, do you mean you have a qualified domain redirecting to your "home" IP address?

if so, could it be your port 80 is blocked by your ISP?

---

### Post by richardhwinter on 2012-04-30
thanks for your reply

Not sure I understand your question. This has nothing to do with ISP (Internet Service Provider ?)
It's all local:
Apache @ localhost
Virtual host set up like this:
<VirtualHost *:80>
	ServerName zettelkasten.test
	ServerAdmin webmaster@localhost
<...>

Server Name registered in /etx/hosts on all machines.

But I guess I'm missing some essential but simple fact.

---

### Post by dchrono on 2012-05-01
to allow incoming connections on port 80

[COLOR=#007800]SERVER_IP=[/COLOR][COLOR=#ff0000]"xxx.xxx.xxx.xxx"[/COLOR] 
iptables -A INPUT -p tcp -s [COLOR=#000000]0[/COLOR]/[COLOR=#000000]0[/COLOR] --sport [COLOR=#000000]1024[/COLOR]:[COLOR=#000000]65535[/COLOR] -d [COLOR=#007800]$SERVER_IP[/COLOR] --dport [COLOR=#000000]80[/COLOR] -m state --state NEW,ESTABLISHED -j ACCEPT 

iptables -A OUTPUT -p tcp -s [COLOR=#007800]$SERVER_IP[/COLOR] --sport [COLOR=#000000]80[/COLOR] -d [COLOR=#000000]0[/COLOR]/[COLOR=#000000]0[/COLOR] --dport [COLOR=#000000]1024[/COLOR]:[COLOR=#000000]65535[/COLOR] -m state --state ESTABLISHED -j ACCEPTto allow outgoing traffic on port 80

to allow outgoing connections to port 80

[COLOR=#007800]SERVER_IP=[/COLOR][COLOR=#ff0000]"xxx.xxx.xxx.xxx"[/COLOR] 
iptables -A OUTPUT -p tcp -s [COLOR=#007800]$SERVER_IP[/COLOR] --sport [COLOR=#000000]1024[/COLOR]:[COLOR=#000000]65535[/COLOR] -d [COLOR=#000000]0[/COLOR]/[COLOR=#000000]0[/COLOR] --dport [COLOR=#000000]80[/COLOR] -m state --state NEW,ESTABLISHED -j ACCEPT 

iptables -A INPUT -p tcp -s [COLOR=#000000]0[/COLOR]/[COLOR=#000000]0[/COLOR] --sport [COLOR=#000000]80[/COLOR] -d [COLOR=#007800]$SERVER_IP[/COLOR] --dport [COLOR=#000000]1024[/COLOR]:[COLOR=#000000]65535[/COLOR] -m state --state ESTABLISHED -j ACCEPT


service iptables restart

however,

 /sbin/iptables -A INPUT -p tcp &#8211;dport 80  -m state &#8211;state NEW -j ACCEPT

 should be enough.

I do the same for port 443, you may want to do the same, hope this helps

---

### Post by richardhwinter on 2012-05-01
Thanks for your help. I hoped I could come back with good news but the issue is persistent.
I tried both of you methods adjusting iptables but it didn't help.
I have attached the current content of iptables on the server machine in case you want to have a look. It's still mystery for me.

The more I think about it I assume the problem isn't on the server but on the client side. 
When I do a trace route there it stops at the client machine and I get no results from a port scan of the server.
How this agrees with the tcpdump showing requests from the client I have no idea.

I'm on a business trip the rest of the week. When my daughter visits at the weekend I will try it with her computer to figure out on which side of the network the problem lies (she has a Mac - not sure whether there is something like the hosts file).

Thanks again for your help - eventually we are getting there -:)

Richard

---

### Post by richardhwinter on 2012-05-05
I'm back again and still no success despite another couple of hours of messing around -:)

My daughter's MAC has no problem to get to my site.
Therefor my theory is that the client has some setting preventing the access to my site.
A traceroute there gives this result:
```

renate@renate-zwei:~$ traceroute zettelkasten.test
traceroute to zettelkasten.test (192.168.1.2), 30 hops max, 60 byte packets
 1  * * *
 2  * * *
and so on for 30 hops

```
A tcpdump on the client shows this:
```

renate@renate-zwei:~$ sudo tcpdump -vvv -i any -s 1600 icmp
tcpdump: listening on any, link-type LINUX_SLL (Linux cooked), capture size 1600 bytes
19:07:29.720089 IP (tos 0xc0, ttl 64, id 50841, offset 0, flags [none], proto ICMP (1), length 576)
    renate-zwei.local > renate-zwei.local: ICMP zettelkasten.test unreachable - need to frag (mtu 1500), length 556
	IP (tos 0x0, ttl 1, id 0, offset 0, flags [DF], proto UDP (17), length 65535)
    renate-zwei.local.59307 > zettelkasten.test.44444: UDP, length 65507

```

I tried all kind of settings for ufw and iptables and I have attached the current content (but even with disabling ufw there is the same "performance").

Another thought: maybe the Samba configuration is messing this up. The client machine is set up as our family file and backup server) an therefor I have added the smb.conf as well.

I hope someone is out there who can help. It would make me really happy.

Thanks in advance
Richard

---

### Post by richardhwinter on 2012-05-06
I finally got it solved!!
Don't ask how many hours I spent googling and messing around with the settings :)
As I did so many changes I can't tell for sure which one solved it.

My best bet: removing firestarter from both the client and the host machine. I didn't know it was there but a check in synaptic showed me it was installed.

Then I did more finetuning of the firewall with ufw based on these excellent sites:
[http://log.logfish.net/node/31](http://log.logfish.net/node/31)
[http://1000umbrellas.com/2010/04/29/how-to-set-up-the-firewall-using-ufw-on-ubuntu-lucid-lynx-server](http://1000umbrellas.com/2010/04/29/how-to-set-up-the-firewall-using-ufw-on-ubuntu-lucid-lynx-server)

Just in case someone stumbles over this thread and wonders how it got solved.

Thanks 
Richard

---


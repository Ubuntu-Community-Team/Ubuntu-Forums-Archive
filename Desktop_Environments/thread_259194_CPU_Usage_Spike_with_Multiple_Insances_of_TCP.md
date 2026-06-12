---
title: "CPU Usage Spike with Multiple Insances of TCP"
date: 2006-09-17
forum: Desktop Environments
---

### Post by cfabbriumd on 2006-09-17
Hi,
     I've been noticeing over the last couple of weeks that my computer has severly slowed down after I have left it on for a day. (Usally I have it on all the time). I clean installed a Dapper in the summer, and I have a lot of server stuff on there like Apache, DHCP and SSH. 

Anyway, it has been acting REALLY slow, the actual login can take ten minutes or more for it to book into Gnome. I've recently noticed there were at least a dozen instances of "TCPD" all clogging up the CPU usage. When I ended them, the system returned to normal speed. This is only a temporary fix, and it does pop back up after awhile. (Also, I don't like having to close a system process without knowing its consequences :confused: )

My two questions are: Why is the happening and how do I get the TCPD to work properly? ](*,)

---

### Post by sktx on 2006-09-17
Why are you running all those services?  It's likely with all those running, listening on half your ports, that your box has been compromised and is being used as a drone, serving files, or being used to carry out DDoS attacks on orphans, nuns and little old ladies. 

You don't like having to close a system process without knowing it's consequences?  What about running several easily exploitable services completely unchecked?

I recommend you format and reinstall, and ask a few folks on the forums how to secure those services before you install them and expose yourself to an internet full of script kiddies who want to add your computer to their botnet so they can flood channels on IRC.

---

### Post by cfabbriumd on 2006-09-17
> **sktx said:**
> Why are you running all those services?  It's likely with all those running, listening on half your ports, that **your box has been compromised and is being used as a drone, serving files, or being used to carry out DDoS attacks on orphans, nuns and little old ladies.**

You don't like having to close a system process without knowing it's consequences?  What about running several easily exploitable services completely unchecked?

**I recommend you format and reinstall**, and ask a few folks on the forums how to secure those services before you install them and expose yourself to an internet full of script kiddies who want to add your computer to their botnet so they can flood channels on IRC.

I appreciate your post, but you still havn't answered my question: Why exactly is it poping up several insances of TCPD and what do I do to stop it.

I would know if my computer is subseptable to and IRC attack (and believe me, I would know because I can get blocked for such things). As for the services, for one reason or another, are needed especially the SSH, which I have run through the configuration file and customied it to my needs and relative security. I'd be willing to shut down the Apache server, but anything else I will need.

Reformatting the computer is out of the question unless I really need to. It takes too much time to get it to what I have now.

I would greatly appreciate a more practical solution to this problem.

---

### Post by sktx on 2006-09-17
> **cfabbriumd said:**
> I appreciate your post, but you still havn't answered my question: Why exactly is it poping up several insances of TCPD and what do I do to stop it.

I would know if my computer is subseptable to and IRC attack (and believe me, I would know because I can get blocked for such things). As for the services, for one reason or another, are needed especially the SSH, which I have run through the configuration file and customied it to my needs and relative security. I'd be willing to shut down the Apache server, but anything else I will need.

Reformatting the computer is out of the question unless I really need to. It takes too much time to get it to what I have now.

I would greatly appreciate a more practical solution to this problem.

Here's something from the man page for tcpd..

[B]NAME
       tcpd - access control facility for internet services

DESCRIPTION
       The tcpd program can be set up to monitor incoming requests for telnet,
       finger, ftp, exec, rsh, rlogin, tftp, talk, comsat and  other  services
       that have a one-to-one mapping onto executable files.

...

       The  program  supports  both  4.3BSD-style sockets and System V.4-style
       TLI.  Functionality may be limited when the protocol underneath TLI  is
       not an internet protocol.

       There  are  two possible modes of operation: execution of tcpd before a
       service started by inetd, or linking a daemon with the  libwrap  shared
       library  as  documented  in  the hosts_access(3) manual page. Operation
       when started by inetd is as follows: whenever  a  request  for  service
       arrives,  the  inetd  daemon  is  tricked into running the tcpd program
       instead of the desired server. tcpd logs  the  request  and  does  some
       additional  checks.  When all is well, tcpd runs the appropriate server
       program and goes away.[/B]

----------

So here's the deal as I see it at first glance:

You're running several services which rely on tcpd for their access control.  you're getting multiple requests from unauthorized clients on the ports these services are running on, and since these clients are likely to be just scripts running dictionary attacks on any insecure computer they find, they're pounding down your door, trying every different username/password combination they can think of.  Either one at a time, and tcpd doesn't exit because it never gets the authentication that it's waiting for, or several at a time, both of which explain why you have 10 instances of the program running.  

------

[B]ACCESS CONTROL
       Optionally, tcpd supports a simple form of access control that is based
       on  pattern  matching.   The access-control software provides hooks for
       the execution of shell commands when a pattern fires.  For details, see
       the hosts_access(5) manual page.

HOST NAME VERIFICATION
       The  authentication  scheme  of  some protocols (rlogin, rsh) relies on
       host names. Some implementations believe the host name  that  they  get
       from any random name server; other implementations are more careful but
       use a flawed algorithm.
[/B]
.....

[B]BUGS
       Some UDP (and RPC) daemons linger around for a while  after  they  have
       finished  their  work,  in case another request comes in.  In the inetd
       configuration file these services are registered with the wait  option.
       Only the request that started such a daemon will be logged.[/B]

-----

So here's what the deal is:  there's a couple files you should set up so that running the services which rely on tcpd isn't equivalent to shooting yourself in the foot...

/etc/hosts.allow
/etc/hosts.deny

check out the man page for hosts_access, hosts.allow, and hosts.deny, as well as the man page for tcpd.  

and bear in mind that, while a lot of folks here on the forums are running linux at least partially because of the increased security, running open, unconfigured services that you don't know how to administer leaves your computer less secure than a windows machine.

---

### Post by cfabbriumd on 2006-09-19
I looked over my system and found something interesting:

First I tried shutting down the Apache2 service one of my less configured service, which led to no results.

Then I noticed something interesting in the system monitor. The arguments for all the instances of the tcpd process started up the smbd service (windows sharing). I tried shutting it down, but it would not let me. Since I didn’t need it anyway because I had the ssh/sftp server, I uninstalled it (it never worked properly anyway so it was just being a waste). Since then (about a day or so), this problem has not come up. I’ll keep an eye on it to see if more problems arise. :-k

What makes this interesting is that I have a Linksys wireless router. No windows sharing ports were forwarded to the computer. In addition the firewall and NAT filtering settings were on. It is impossible for others to access the local network, so I find this a little perplexing. Could it also be a malfunctioning smbd?? :? 

If I can recall correctly, the smbd was configured in the init.d directory, which is monitored by tcpd. Ill pay attention closer next time to the process arguments. #-o

---


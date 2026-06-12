---
title: "Microsoft-ds"
date: 2009-04-21
forum: General Help
---

### Post by kibster on 2009-04-21
How come I am getting hits on my FIRESTARTER from Microsoft-ds

Anyone know why... Happens everyday. 

Russ

---

### Post by cariboo on 2009-04-21
It seems if you download anything from any of Microsofts web sites you keeps getting probes from them. Nothing to worry about.

Jim

---

### Post by Yashiro on 2009-04-21
Do you use Samba or have Windows computers on your network?
If so that's why.

---

### Post by kibster on 2009-04-21
Nope... Nothing MS , This is new install only week or so old.. Before this though I was running xp and got tired of the usual garbage that goes with using windows...and had asked their support team for help which they gave me but could not fix the problem..when they called here a couple of weeks ago I told them I was switching to linux.. They said they felt bad. But I was tired of having to buy 70-80.00 virus programs with little resuls...cost more to keep going than it was worth it...

So I wonder if there keeping an eye my box. But nothing MS

could someone name there box a Microsoft-Ds ..and it show up that way.

I also am getting hits from a SAMBA box too... Am I the only one getting this sort of thing going on or does everyone have these sorts of hits on them.

Thanks
Russ

---

### Post by Yashiro on 2009-04-21
Do *netstat -tuaevpn*. If you have 445 as listening then either you ARE running samba or you have another daemon/trojan running.
Trojan is unlikely, it's probably samba. Paste the output of *sudo lsof -i -P -n*

Afterwards try *sudo /etc/init.d/samba stop* then run *netstat-tuaevpn* again.

---

### Post by kibster on 2009-04-22
Here are the results . I don't know what it means or what it says.
Please explain.But I did what you asked hopefully it means something.

Russ


Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       User       Inode       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      0          14269       -               
tcp        0      0 24.56.205.148:34721     74.125.95.18:80         ESTABLISHED 1000       19642       5844/firefox    
tcp        0      0 24.56.205.148:34719     74.125.95.18:80         ESTABLISHED 1000       19622       5844/firefox    
udp        0      0 0.0.0.0:68              0.0.0.0:*                           0          15557       -               
udp        0      0 0.0.0.0:46930           0.0.0.0:*                           110        14175       -               
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           110        14174  

:~$ sudo lsof -i -P -n
[sudo] password for kibzz: 
Sorry, try again.
[sudo] password for kibzz: 
COMMAND    PID  USER   FD   TYPE DEVICE SIZE NODE NAME
avahi-dae 4471 avahi   14u  IPv4  14174       UDP *:5353 
avahi-dae 4471 avahi   15u  IPv4  14175       UDP *:46930 
cupsd     4515  root    2u  IPv4  14269       TCP 127.0.0.1:631 (LISTEN)
dhclient  4942  root    5w  IPv4  15557       UDP *:68 
firefox   5844 kibzz   43u  IPv4  21577       TCP 24.56.205.148:42175->74.125.95.102:80 (ESTABLISHED)
firefox   5844 kibzz   59u  IPv4  19622       TCP 24.56.205.148:34719->74.125.95.18:80 (ESTABLISHED)

:~$ COMMAND    PID  USER   FD   TYPE DEVICE SIZE NODE NAME
bash: COMMAND: command not found
:~$ avahi-dae 4471 avahi   14u  IPv4  14174       UDP *:5353 
bash: avahi-dae: command not found
:~$ avahi-dae 4471 avahi   15u  IPv4  14175       UDP *:46930 
bash: avahi-dae: command not found
:~$ cupsd     4515  root    2u  IPv4  14269       TCP 127.0.0.1:631 (LISTEN)
bash: syntax error near unexpected token `('
:~$ dhclient  4942  root    5w  IPv4  15557       UDP *:68 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
SIOCSIFADDR: Permission denied
*:68: ERROR while getting interface flags: No such device
*:68: ERROR while getting interface flags: No such device
SIOCSIFADDR: Permission denied
UDP: ERROR while getting interface flags: No such device
UDP: ERROR while getting interface flags: No such device
SIOCSIFADDR: Permission denied
15557: ERROR while getting interface flags: No such device
15557: ERROR while getting interface flags: No such device
SIOCSIFADDR: Permission denied
IPv4: ERROR while getting interface flags: No such device
IPv4: ERROR while getting interface flags: No such device
SIOCSIFADDR: Permission denied
5w: ERROR while getting interface flags: No such device
5w: ERROR while getting interface flags: No such device
SIOCSIFADDR: Permission denied
root: ERROR while getting interface flags: No such device
root: ERROR while getting interface flags: No such device
SIOCSIFADDR: Permission denied
4942: ERROR while getting interface flags: No such device
4942: ERROR while getting interface flags: No such device
Open a socket for LPF: Operation not permitted
kibzz@toy-desktop:~$ firefox   5844 kibzz   43u  IPv4  21577       TCP 24.56.205.148:42175->74.125.95.102:80 (ESTABLISHED)
bash: syntax error near unexpected token `('
kibzz@toy-desktop:~$ firefox   5844 kibzz   59u  IPv4  19622       TCP 24.56.205.148:34719->74.125.95.18:80 (ESTABLISHED)

---

### Post by Yashiro on 2009-04-22
There doesn't seem to be anything overly strange apart from those SIOCS errors.

Port 631 is the cups printing service.
445, as mentioned, is usually samba/shared folders.

The errors seem to stem from a missing reference to a network device. I've not encountered it before myself. You might need to look into that but I don't think you have anything else to worry about.

---

### Post by kibster on 2009-04-23
I'm so new at this that I question everything.. Thanks for you's that have comment , Its a relief to have someone around to bounce things  off of. It puts  my mind at ease.. 

Thank you very much for your input..

Russ

---


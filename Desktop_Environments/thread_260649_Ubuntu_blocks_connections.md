---
title: "Ubuntu blocks connections:"
date: 2006-09-19
forum: Desktop Environments
---

### Post by capo on 2006-09-19
Ok so used to use breezy for my linux box but i decided to upgrade to dapper.
Backed up all my files, reformatted, reinstalled, etc.

NOTE ON THE INSTALL:

the new partitioner is AWFULL uggh it failed every time i tried to make a swap partition and it had no diagnostic tools etc. Tankfully i just opened a terminal and used fdisk to partition.

Anyway after installing i copied my old firewall script over and put it in /etc/network/if-up.d

it reads:

#!/bin/sh

# some handy variables
WAN_IF=eth0
LAN_IF=eth1
LAN_NET=192.168.1.1/24

#default chain polocies
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT
iptables -F

# Allow localhost traffic
iptables -A INPUT -i lo -j ACCEPT

#Allow lan traffic
iptables -A INPUT -i $LAN_IF -j ACCEPT

#Allow outgoing connection from LAN
iptables -A FORWARD -o $WAN_IF -p tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmtu
iptables -A FORWARD -i $LAN_IF -s $LAN_NET -o $WAN_IF -j ACCEPT

#Allow return packets from the internet to the router/lan
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -i $WAN_IF -m state --state RELATED,ESTABLISHED -j ACCEPT

#Enable NAT for outgoing lan traffic
iptables -t nat -A POSTROUTING -o $WAN_IF -j MASQUERADE

#enable ip_fowarding in the kernel
echo 1 >/proc/sys/net/ipv4/ip_forward

I also have another script in the same folder which reads:

#!/bin/sh

#This script open vairous ports

#Bittorrent
iptables -A INPUT -p tcp --dport 6881:6999 -j ACCEPT
iptables -A OUTPUT -p tcp --source-port 6881:6999 -j ACCEPT

#ssh
iptables -A INPUT -p tcp --dport 22 -j ACCEPT


Now even if i change:

iptables -P INPUT DROP

to

iptables -P INPUT ACCEPT

Now after running thses scripts or restarting my NIC to autmoaticaly run them Ubuntu still blocks ALL connection made from other computer, I CANT EVEN SSH TO MYSELF!! i get 'connection refused'

Now according to the ubuntu desktop guide

"A firewall protects a computer system from unauthorized access. It is not normally necessary to install a firewall on an Ubuntu system, because access to the system is closed by default."

Right. So how do i disable this 'default closure' so that my script can handle the firewalling. And no i dont want to install firestarter. I find just using iptables is much more powerfull and much preferred.

---

### Post by jd65pl on 2006-09-19
Is your ssh server running?

Try ```
ssh localhost
```

On the server machine to find out, appologies if any help appears patronising or condesending but it is difficult to judge someones ability over an internet connection

---

### Post by capo on 2006-09-19
firstly i already tried ssh'ing myself using

ssh 192.168.1.1 (my lan address)
ssh 210.18.228.134 (my wan adress)
ssh 127.0.0.1 (localhost)
and
ssh localhost

all of which return 

"ssh: connect to host 127.0.0.1 port 22: Connection refused"

and yes i have checked to make sure the daemon is running. And it's ok you didn't seem patronizing, it's a very logical thing to check. 

What i dont get is that this is a huge issue and appears to be in the default install as i have changed NOTHING since installing except for running my firewall script which i listed above, and yet i havent seen any other posts about it.

---

### Post by jd65pl on 2006-09-19
Try 

```
sudo netstat -lp | grep ssh
```

To see if a program is listening for connections via ssh

---

### Post by capo on 2006-09-19
> **jd65pl said:**
> Try 

```
sudo netstat -lp | grep ssh
```

To see if a program is listening for connections via ssh

unix  2      [ ACC ]     STREAM     LISTENING     12309    5002/ssh-agent      /tmp/ssh-tAfsMj4960/agent.4960

so yes.

---

### Post by jd65pl on 2006-09-19
Would it be possible for you to use nmap to see if the port is accessable via the client machine.

I'm pretty sure its in the repositories. Install it to the client then use
```
nmap xxx.xxx.xxx.xxx
```
Where xxx.xxx.xxx.xxx is your IP address.

Did you run
```
sudo netstat -lp | grep ssh
```

On the client or server computer?

Thanks

J

---

### Post by capo on 2006-09-19
> **jd65pl said:**
> Would it be possible for you to use nmap to see if the port is accessable via the client machine.

I'm pretty sure its in the repositories. Install it to the client then use
```
nmap xxx.xxx.xxx.xxx
```
Where xxx.xxx.xxx.xxx is your IP address.

Did you run
```
sudo netstat -lp | grep ssh
```

On the client or server computer?

Thanks

J

As far as the nmap, i ssh'd over to my FC5 machine and ran it from there, it was already installed it being fc5 and all, the output from nmap was:

Starting Nmap 4.03 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2006-09-19 21:14 EST
All 1674 scanned ports on 192.168.1.1 are: closed

and for the netstat yes i ran it on the server. 

for future refernce i am on the server, but i have a moniter pluged into each and my headphones pluged into FC5 machine, watching scrubs while i post on the forums from the ubuntu server machine.

---

### Post by jd65pl on 2006-09-19
I dont think that is a correct output from nmap, it should inform you of which ports are open? can you nmap localhost from your server and post the output?

Thanks

J

---

### Post by capo on 2006-09-19
> **jd65pl said:**
> I dont think that is a correct output from nmap, it should inform you of which ports are open? can you nmap localhost from your server and post the output?

Thanks

J

ohh right sorry i did nmap i just pasted the wrong output. Ive updated the previous post with the correct output now.

The v much for all ure hlp btw.

---

### Post by jd65pl on 2006-09-19
I'm at work right now so I dont have a machine to test on! Win2000 all the way! I will try to give some more assistance but the symptoms lend them selves to:

A: The SSH server isn't on
or
B: IPtables is not configured correctly to accept the SSH connection.

I don't know too much about iptables is there no chance of giving firestarter a go just to see if it can configure IPtables better?

Thanks

J

---

### Post by jd65pl on 2006-09-19
Hey,

Have you got the connection to work yet?

---

### Post by jd65pl on 2006-09-20
I just tried to replicate your problems and i get the error when I try to open an ssh connection to a pc with ssh installed but not turned on.

Try ```
sshd
``` on the server machine. then
```
ssh localhost
```
to see if you can make a connection

J

---

### Post by capo on 2006-10-07
ohh yeah sorry about not replying i totaly forgot about this thread. It turns out i jsut didn't have sshd installed, which to means seem unbeleveiable that a linux distro could come without sshd, that like my favourite feature of linux! Anyway i installed it an it works dandy now.

---


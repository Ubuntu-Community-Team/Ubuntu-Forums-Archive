---
title: "Can't access or ping localhost"
date: 2009-02-28
forum: General Help
---

### Post by djbon2112 on 2009-02-28
If I ping "localhost" all my packets are dropped. If I try to access a webserver on localhost, it fails and times out. I think the problem is iptables, as I've followed the guide [http://ubuntuforums.org/archive/index.php/t-197154.html](http://ubuntuforums.org/archive/index.php/t-197154.html) before, however, now not even that works. The webserver is up and running for sure. I'd like to completely remove iptables, but for now just a workaround will suffice. Any suggestions?

---

### Post by DGortze380 on 2009-02-28
> **djbon2112 said:**
> If I ping "localhost" all my packets are dropped. If I try to access a webserver on localhost, it fails and times out. I think the problem is iptables, as I've followed the guide [http://ubuntuforums.org/archive/index.php/t-197154.html](http://ubuntuforums.org/archive/index.php/t-197154.html) before, however, now not even that works. The webserver is up and running for sure. I'd like to completely remove iptables, but for now just a workaround will suffice. Any suggestions?

first can you post the output of 
cat /etc/network/interfaces

I'll go look at that guide.

---

### Post by djbon2112 on 2009-02-28
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        gateway 192.168.0.1

```

And my /etc/hosts for good measure

```
127.0.0.1	localhost
127.0.0.1	W01.0.100-Zeus

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by DGortze380 on 2009-02-28
> **djbon2112 said:**
> ```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        gateway 192.168.0.1

```

And my /etc/hosts for good measure

```
127.0.0.1	localhost
127.0.0.1	W01.0.100-Zeus

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Please bare with me, and I'll try to help if I can.

I'm familiar with firewalls, but mostly Cisco, not iptables, so I've got to look up syntax and commands as I go.

For starters, lets see your firewall rules
Need the output of sudo iptables -L

---

### Post by djbon2112 on 2009-02-28
> **DGortze380 said:**
> Please bare with me, and I'll try to help if I can.

I'm familiar with firewalls, but mostly Cisco, not iptables, so I've got to look up syntax and commands as I go.

For starters, lets see your firewall rules
Need the output of sudo iptables -L

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination     
```

As a fix I tried setting every policy open, but it hasn't changed anything.

---

### Post by DGortze380 on 2009-02-28
> **djbon2112 said:**
> ```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination     
```

As a fix I tried setting every policy open, but it hasn't changed anything.

Ok, I may be wrong, but to be sure, I'm going to assume iptables uses an implicit deny.

I'm just using this wiki, I'll try to piece together some commands that will either fix to problem or rule out iptables as the problem. [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by djbon2112 on 2009-02-28
I've actually got it. I just disabled ufw (the Ubuntu firewall) and restarted, and now I can access everything. I have zero need for a local software firewall so it's no loss, and before I was trying to disable iptables itself and not ufw.

If anyone's interested in how I did it, it's just:

```

# ufw disable
```

...then a restart, and it should be disabled.

But thanks for the help DGortze380! :)

---

### Post by DGortze380 on 2009-02-28
// Comments in C++ Style
// Commands in Code Blocks

// Allow established session to receive traffic
```

sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

```

// Allow incoming web traffic
```

sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT

```

// Allow incoming ICMP packets
```

sudo iptables -A INPUT -p icmp -j ACCEPT

```

// Allow all outgoing traffic tcp
```

sudo iptables -A OUTPUT -p tcp -j ACCEPT

```

// Allow all outgoing traffic udp
```

sudo iptables -A OUTPUR -p udp -j ACCEPT

```

// Allow all outgoing traffic icmp
```

sudo iptables -A OUTPUR -p icmp -j ACCEPT

```

If any of these don't work, let me know, we may have to tweak them. I dont have a virtual machine working right now

---

### Post by DGortze380 on 2009-02-28
> **djbon2112 said:**
> I've actually got it. I just disabled ufw (the Ubuntu firewall) and restarted, and now I can access everything. I have zero need for a local software firewall so it's no loss, and before I was trying to disable iptables itself and not ufw.

If anyone's interested in how I did it, it's just:

```

# ufw disable
```

...then a restart, and it should be disabled.

But thanks for the help DGortze380! :)

Glad you're running. I'll leave the firewall rules incase anyone wants them.

---


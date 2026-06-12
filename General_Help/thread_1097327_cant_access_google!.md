---
title: "cant access google!"
date: 2009-03-15
forum: General Help
---

### Post by orlox on 2009-03-15
Well, this is a strange one (or at least it seems very starnge to me!)

I have two hp pavilion notebooks, and I cant access google from any of them! One is running intrepid, and the other jaunty, and suddenly both of them stopped displaying google related pages. When accessing gmail for example, it redirects to [https://www.google.com/accounts/ServiceLogin?...etc](https://www.google.com/accounts/ServiceLogin?...etc)... and then it fails to load saying it cant find the adress at google.com

Under the same network I have proved a windows pc connected with the wired connection and it opens google.com, also, I proved a windows laptop connected with the wireless and it also worked.

Now, for the wierd part...I can ping to google without package loss:
```

pablo@warifaifa:~$ ping google.cl
PING google.cl (216.239.59.104) 56(84) bytes of data.
64 bytes from 216.239.59.104: icmp_seq=1 ttl=241 time=250 ms
64 bytes from 216.239.59.104: icmp_seq=2 ttl=241 time=254 ms
64 bytes from 216.239.59.104: icmp_seq=3 ttl=241 time=264 ms
64 bytes from 216.239.59.104: icmp_seq=4 ttl=241 time=250 ms
64 bytes from 216.239.59.104: icmp_seq=5 ttl=241 time=837 ms
64 bytes from 216.239.59.104: icmp_seq=6 ttl=241 time=250 ms
64 bytes from 216.239.59.104: icmp_seq=7 ttl=241 time=253 ms
64 bytes from 216.239.59.104: icmp_seq=8 ttl=241 time=254 ms
64 bytes from 216.239.59.104: icmp_seq=9 ttl=241 time=256 ms
64 bytes from 216.239.59.104: icmp_seq=10 ttl=241 time=252 ms
64 bytes from 216.239.59.104: icmp_seq=11 ttl=241 time=251 ms
64 bytes from 216.239.59.104: icmp_seq=12 ttl=241 time=252 ms
64 bytes from 216.239.59.104: icmp_seq=13 ttl=241 time=251 ms
64 bytes from 216.239.59.104: icmp_seq=14 ttl=241 time=250 ms
^C64 bytes from 216.239.59.104: icmp_seq=15 ttl=241 time=248 ms

--- google.cl ping statistics ---
15 packets transmitted, 15 received, 0% packet loss, time 75920ms
rtt min/avg/max/mdev = 248.130/292.023/837.273/145.771 ms

```
And also, today I used a different wireless network and I had no problems connecting to google.

Really dont know what could be going wrong here, and why both computers starting suffering from this with no apparent reason!

oh! and as another detail...proved both with konqueror and firefox. Same result in both of them.

Please help!

---

### Post by DGortze380 on 2009-03-15
> **orlox said:**
> Well, this is a strange one (or at least it seems very starnge to me!)

I have two hp pavilion notebooks, and I cant access google from any of them! One is running intrepid, and the other jaunty, and suddenly both of them stopped displaying google related pages. When accessing gmail for example, it redirects to [https://www.google.com/accounts/ServiceLogin?...etc](https://www.google.com/accounts/ServiceLogin?...etc)... and then it fails to load saying it cant find the adress at google.com

Under the same network I have proved a windows pc connected with the wired connection and it opens google.com, also, I proved a windows laptop connected with the wireless and it also worked.

Now, for the wierd part...I can ping to google without package loss:
```

pablo@warifaifa:~$ ping google.cl
PING google.cl (216.239.59.104) 56(84) bytes of data.
64 bytes from 216.239.59.104: icmp_seq=1 ttl=241 time=250 ms
64 bytes from 216.239.59.104: icmp_seq=2 ttl=241 time=254 ms
64 bytes from 216.239.59.104: icmp_seq=3 ttl=241 time=264 ms
64 bytes from 216.239.59.104: icmp_seq=4 ttl=241 time=250 ms
64 bytes from 216.239.59.104: icmp_seq=5 ttl=241 time=837 ms
64 bytes from 216.239.59.104: icmp_seq=6 ttl=241 time=250 ms
64 bytes from 216.239.59.104: icmp_seq=7 ttl=241 time=253 ms
64 bytes from 216.239.59.104: icmp_seq=8 ttl=241 time=254 ms
64 bytes from 216.239.59.104: icmp_seq=9 ttl=241 time=256 ms
64 bytes from 216.239.59.104: icmp_seq=10 ttl=241 time=252 ms
64 bytes from 216.239.59.104: icmp_seq=11 ttl=241 time=251 ms
64 bytes from 216.239.59.104: icmp_seq=12 ttl=241 time=252 ms
64 bytes from 216.239.59.104: icmp_seq=13 ttl=241 time=251 ms
64 bytes from 216.239.59.104: icmp_seq=14 ttl=241 time=250 ms
^C64 bytes from 216.239.59.104: icmp_seq=15 ttl=241 time=248 ms

--- google.cl ping statistics ---
15 packets transmitted, 15 received, 0% packet loss, time 75920ms
rtt min/avg/max/mdev = 248.130/292.023/837.273/145.771 ms

```
And also, today I used a different wireless network and I had no problems connecting to google.

Really dont know what could be going wrong here, and why both computers starting suffering from this with no apparent reason!

oh! and as another detail...proved both with konqueror and firefox. Same result in both of them.

Please help!

Try putting this into the address bar of your browser

[http://64.233.161.147/](http://64.233.161.147/)

or this one if that doesn't work

[http://64.233.161.104/](http://64.233.161.104/)

or this one if that doesn't work

[http://64.233.161.99/](http://64.233.161.99/)

---

### Post by orlox on 2009-03-15
That gives me google!

Then it should be just a name resolving issue. As far as I know that should mean an issue with the /etc/hosts configuration, however, there are just at they're defaults:

```

pablo@warifaifa:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	warifaifa

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
pablo@warifaifa:~$ cat /etc/hosts.allow 
# /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
pablo@warifaifa:~$ cat /etc/hosts.deny
# /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.
#                  See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: some.host.name, .some.domain
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
# The PARANOID wildcard matches any host whose name does not match its
# address.

# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID

```

---

### Post by DGortze380 on 2009-03-15
> **orlox said:**
> That gives me google!

Then it should be just a name resolving issue. As far as I know that should mean an issue with the /etc/hosts configuration, however, there are just at they're defaults:

```

pablo@warifaifa:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	warifaifa

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
pablo@warifaifa:~$ cat /etc/hosts.allow 
# /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
pablo@warifaifa:~$ cat /etc/hosts.deny
# /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.
#                  See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: some.host.name, .some.domain
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
# The PARANOID wildcard matches any host whose name does not match its
# address.

# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID

```

Are the machine that are having issues with Google set up with DHCP or Static IPs?

---

### Post by orlox on 2009-03-15
Im using DHCP, and also, there is no there site showing this behavior (or at least, none of the sites I use are showing it)

---

### Post by Gunman1982 on 2009-03-15
You can check which nameservers you use by looking at the file '/etc/resolv.conf'.

---

### Post by orlox on 2009-03-15
I had forgotten aboud resolv.conf this is what it has:

# Generated by NetworkManager
nameserver 192.168.0.1

---

### Post by Hobgoblin on 2009-03-15
I think it's a problem logging in to google.cl

Clear your cookies and try again.

---

### Post by orlox on 2009-03-15
Nope, its not that. Removed also the cache adn it didnt help

---

### Post by orlox on 2009-03-15
Something I just noticed. I can access al of googles subdomains with no problem at all (i.e. images.google.com, video.google.com, maps.google.com, etc...)

gmail.google.com also works, but redirects to google.com with brings back a cant find server at google.com

---

### Post by orlox on 2009-03-15
Perhaps this is of some use...The output of the host command:
```

host www.google.com
;; Truncated, retrying in TCP mode.
;; Connection to 192.168.0.1#53(192.168.0.1) for www.google.com failed: connection refused.

```

---

### Post by orlox on 2009-03-16
I found a similar problem described here (found this using live search since i cant use google...)

[http://www.networknewz.com/networknewz-10-20070928ADNSPuzzler.html](http://www.networknewz.com/networknewz-10-20070928ADNSPuzzler.html)

As mentioned there, i tried this:

```

pablo@warifaifa:~/Desktop/fallout$ dig +ignore www.google.com

; <<>> DiG 9.5.1-P1 <<>> +ignore www.google.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 64251
;; flags: qr tc rd ra; QUERY: 1, ANSWER: 25, AUTHORITY: 4, ADDITIONAL: 0

;; QUESTION SECTION:
;www.google.com.			IN	A

;; ANSWER SECTION:
www.google.com.		604219	IN	CNAME	www.l.google.com.
www.l.google.com.	19	IN	A	190.45.0.23
www.l.google.com.	19	IN	A	190.45.0.24
www.l.google.com.	19	IN	A	190.45.0.25
www.l.google.com.	19	IN	A	190.45.0.26
www.l.google.com.	19	IN	A	190.45.0.27
www.l.google.com.	19	IN	A	190.45.0.28
www.l.google.com.	19	IN	A	190.45.0.29
www.l.google.com.	19	IN	A	190.45.0.30
www.l.google.com.	19	IN	A	190.45.0.31
www.l.google.com.	19	IN	A	190.45.0.32
www.l.google.com.	19	IN	A	190.45.0.33
www.l.google.com.	19	IN	A	190.45.0.34
www.l.google.com.	19	IN	A	190.45.0.35
www.l.google.com.	19	IN	A	190.45.0.36
www.l.google.com.	19	IN	A	190.45.0.37
www.l.google.com.	19	IN	A	190.45.0.38
www.l.google.com.	19	IN	A	190.45.0.39
www.l.google.com.	19	IN	A	190.45.0.16
www.l.google.com.	19	IN	A	190.45.0.17
www.l.google.com.	19	IN	A	190.45.0.18
www.l.google.com.	19	IN	A	190.45.0.19
www.l.google.com.	19	IN	A	190.45.0.20
www.l.google.com.	19	IN	A	190.45.0.21
www.l.google.com.	19	IN	A	190.45.0.22

;; AUTHORITY SECTION:
l.google.com.		85819	IN	NS	e.l.google.com.
l.google.com.		85819	IN	NS	f.l.google.com.
l.google.com.		85819	IN	NS	g.l.google.com.
l.google.com.		85819	IN	NS	a.l.google.com.

;; Query time: 12 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Mon Mar 16 01:09:53 2009
;; MSG SIZE  rcvd: 500

```
So, using the +ignore flag, the domain can be resolved. According to the man page, the flag does this:
> Ignore truncation in UDP responses instead of retrying with TCP. By default, TCP retries are performed.


Don't really know what it means and how it could solve my problem though...

---

### Post by orlox on 2009-03-16
Found a solution for this (more like a workaround though)
Other people have this issue, and I found a launchpad bug for it:

[https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/327364](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/327364)

The workaround (wich I also posted at that bug report) is to append the lines:

nameserver 208.67.222.222
nameserver 208.67.220.220

To your /etc/resolv.conf

---

### Post by jellylogix on 2009-03-16
Maybe this is really far off from anything that could technically be considered "help", but what if you tried setting your IP to Static, and therefore your DNS to your gateway address.

so IP = 192.168.1.50 
   Gateway = 192.168.1.1 (or whatever your router address is)
   Subnet = 255.255.255.0

   And  make the DNS Server the same as the Gateway address.

If it can resolve the IP "version" of google, yet can't resolve "google.com/mail" then I'm thinking it has to do with the nameserver (DNS), so try setting it to your gateway.

Sorry if this doesn't make any logical sense to gurus that know if this will do anything or not. It's a guess, and it won't hurt to try.

---

### Post by orlox on 2009-03-16
> 
Maybe this is really far off from anything that could technically be considered "help", but what if you tried setting your IP to Static, and therefore your DNS to your gateway address.

so IP = 192.168.1.50
Gateway = 192.168.1.1 (or whatever your router address is)
Subnet = 255.255.255.0

And make the DNS Server the same as the Gateway address.

If it can resolve the IP "version" of google, yet can't resolve "google.com/mail" then I'm thinking it has to do with the nameserver (DNS), so try setting it to your gateway.

Sorry if this doesn't make any logical sense to gurus that know if this will do anything or not. It's a guess, and it won't hurt to try.


Thanks for your suggestion, but I already found a solution (if it starts failing though, Ill surely try this ;))

---

### Post by Hobgoblin on 2009-03-16
> **orlox said:**
> Found a solution for this (more like a workaround though)
Other people have this issue, and I found a launchpad bug for it:

[https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/327364](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/327364)

The workaround (wich I also posted at that bug report) is to append the lines:

nameserver 208.67.222.222
nameserver 208.67.220.220

To your /etc/resolv.conf

That's using OpenDNS instead of your regular DNS servers, which suggests it's a problem with the DNS server provided by your ISP.

---

### Post by ugm6hr on 2009-03-16
> **Hobgoblin said:**
> That's using OpenDNS instead of your regular DNS servers, which suggests it's a problem with the DNS server provided by your ISP.

Indeed.

Hence this is not a bug at all, but a problem with your default (i.e. ISP) name servers.

The fact that your Windows machines resolve the IP OK using the default ISP name server is bizarre.  Perhaps an ipv6 issue?  Although I would be surprised.

---

### Post by Gunman1982 on 2009-03-16
Rather than blaming your isp I would take a look at the router, did you read the whole passage of the link you posted?
> What do we know so far? The answer from UDP (the default) is larger than will fit in the UDP packet. My Verizon router apparently doesn't want to use TCP for DNS. Windows works.. does Windows use a different size? Let's try to find out.. 

That's as far as I've been able to get so far. It looks like Windows might use a different udp packet size (though not for nslookup). I found "dig" for Windows, but couldn't get it to work.. so I need better Windows tools to find out more.. 

But if providing static dns helps, go for it.

---

### Post by orlox on 2009-03-16
Truth be told, im not sure if its the router in this case what changed. My router has stayed untouched for quite long, and both computers starting showing this behavior simultaneously, so I believe something fishy is going on with the ISP...

On the other hand, my workaround has a problem...Every time I restart my laptop and connect to the wireless, networkmanager overwrites my resolv.conf file!

---

### Post by ugm6hr on 2009-03-16
Look at number 8 here: [https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)

---

### Post by orlox on 2009-03-16
> Look at number 8 here: [https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)

Perfect! now my /etc/resolv.conf includes the opendns servers after reboot.

Thanks!

---


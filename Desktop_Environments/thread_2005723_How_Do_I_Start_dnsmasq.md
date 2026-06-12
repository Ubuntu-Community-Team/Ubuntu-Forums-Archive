---
title: "How Do I Start dnsmasq"
date: 2012-06-18
forum: Desktop Environments
---

### Post by Acharn on 2012-06-18
Yesterday, following a suggestion I got here, I installed dnsmasq to use as a caching nameserver. Yesterday it seemed to work pretty well, given the lousy network I have to use. Today, to my surprise, I was seeing the same "looking up ..." in my status line as before. Eventually I ran "ps ax | grep dnsmasq," and there wasn't any process running. So I tried various commands that I found in howto's. Every command to start or restart dnsmasq produced the same error message:
```
 * Restarting DNS forwarder and DHCP server dnsmasq                             
dnsmasq: failed to create listening socket for port 53: Address already in use
                                                                         [fail]
```

I've restarted the computer, no joy. Still no dnsmasq process. The Ubuntu documentation isn't helpful. In fact it's a confusing mess. Worse than the man pges I was grappling with back in the 80s. I find from [https://sokratisg.wordpress.com/2012/03/31/ubuntu-precise-12-04-get-rid-of-nms-dnsmasq-and-setup-your-own](https://sokratisg.wordpress.com/2012/03/31/ubuntu-precise-12-04-get-rid-of-nms-dnsmasq-and-setup-your-own) that there was a change in Network Manager in Ubuntu 12.04, which is what I'm using, and I followed his direction to comment out the line in NetworkManager.conf that should be congrolling... well, something.

I don't know. Yesterday, before I installed dnsmasq, there was a process named dnsmasq running. there was no file /etc/dnsmasq.conf. It did not seem to be working as a caching nameserver. After I installed dnsmasq there was a process named dnsmazq, and it seemed to be working as a caching nameserver after I follwed the instructions in the Ubuntu docs to set it up. Today there is no process named dnsmasq and I can't seem to start one. Has anybody succeeded in setting this up?

---

### Post by Acharn on 2012-06-18
OK, since posting the above I've found the discussion at [https://blueprints.launchpad.net/ubuntu/+spec/foundations-p-dns-resolving](https://blueprints.launchpad.net/ubuntu/+spec/foundations-p-dns-resolving). It seems dns caching was purposely turned off in the default dnsmasq. Reading the comments there I feel like this decision was made by people who have pretty good ISP's and, especially, have fast connections. I live in Thailand, my connection is supposed to be 6Mbps, but because of heavy usage a lot of packets are dropped, so connections really are much slower. Using a program called namebench I found a couple of name servers that are faster that OpenDNS -- average 1910 milliseconds rather than 2000 milliseconds. I find about 20% of my connections return Server Not Found errors in my browser and it's common to see the status line showing "looking up ..." five seconds after that address was just looked up. Sometimes after one lookup, looking up the same location will take more than thirty seconds -- or return a Server Not Found error. It just took me fifteen minutes to connect again to this forum after posting the post above.

I'm not happy with turning off caching. I'm not on a network, and I don't care if someone sees what domains I've been looking up. For a while yesterday dnsmasq seemed to be working, and my browsing was faster with fewer errors. Is there anything I can do to override the 12.04 default setup? Is there any way to have caching? If I have to I'll set up my own BIND9 daemon, but now that I've found out about dnsmasq I'm really irritated that I have to.

---

### Post by Acharn on 2012-08-17
In discussion on another thread, another poster told me that the problem (dnsmasq does not allow cashing) is being solved in Ubuntu 12.10, so this thread should be ended.

---

### Post by hawaiiman on 2012-09-29
@Acharn I'm in LOS also. From the high level of self justifying I've seen from the Ubuntu "gurus" about this issue I seriously doubt it will be fixed. I am attempting a server for my school network. After the problems I've had with 12.04, I'm a little gunshy about leaping into 12.10.

---

### Post by Acharn on 2012-09-30
I used Debian starting back in 1996 but switched over to FreeBSD after talking to a guy who claimed the Linux kernel was too unstable for his network (ran into him years later and he said he had switched back to Linux because FreeBSD was too slow). FreeBSD worked great, although I was basically just using it in place of a router for our Windows machines. FreeBSD really required a lot more tinkering with configuration files and most everything had to be done through the terminal, but I loved that I could sit at my desk with my Windows XP machine and use PuTTY to connect with my FreeBSD machine and run everything. I really like Ubuntu for a desktop machine (well, there are a couple of Windows games I can't run in Wine and miss) but I haven't had any reason to think about how good it would be for supporting a network. FreeBSD at the time didn't have good desktop support and after I left the school changed their budgeting policy and bought decent hardware.

For this problem with DNSMasq I've found a couple of helps. Don't know if you've noticed, but here in Thailand there's a block of some sort on [www.rollingstone.com](www.rollingstone.com). Don't know where it happens, apparently one of the international routers or maybe the Rolling Stone server, it doesn't seem to be the Thai censorship, but I was annoyed because I couldn't read Matt Taibbi's rants. I discovered that if I put Rolling Stone in my hosts file I can bypass the DNS lookup and connect. Second, my ISP (3BB) has increased the speed on their cheap account to 10Mbps, which seems to help. Still lots of frustration on the weekends, though.

---


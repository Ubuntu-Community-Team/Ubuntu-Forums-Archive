---
title: "DNS name resolution fails for ping and ssh"
date: 2009-03-29
forum: General Help
---

### Post by gaebriel on 2009-03-29
Hi, I'm experiencing an interesting error when trying to ping or SSH to a host by using its FQDN. The problem is most annoying since I have multiple domains with similar hostnames so when I try to ssh to them, I need to make sure I'm hitting the right one. For example, I have mail servers at each of these domains I support called mx1.domain1.com, mx1.domain2.com, mx1.domain3.com... 

Here are the contents of my /etc/resolv.conf file: 
```

search domain1.com domain2.com domain3.com domain4.com
nameserver 10.1.1.2
```

Using the host command, running `host mx1` returns the IP address of mx1.domain1.com, as expected, but of course, that's all it returns. Running `host mx1.domain1.com` returns the correct IP for the mail server in domain1.com, as well. Running `host mx1.domain2.com` returns the correct IP for the mail server in domain2.com. The 'host' command returns all the values one would expect it to. ping and ssh on the other hand, do not. I manage the DNS server at 10.1.1.2 and it has all the appropriate data in the bind zone files. 

Here's what happens: 
1. pinging mx1 returns successful ping results for the IP of mx1.domain1.com. 
2. pinging mx1.domain1.com simply fails with an unknown host error; pinging mx1.domain2.com also fails with an unknown host error. 
3. running ssh user@mx1 connects me to the mx1.domain1.com box
4. running ssh [email]user@mx1.domain1.com[/email], [email]user@mx1.domain2.com[/email]... fails with "name or service not known" error. 

If the host command resolves the IPs correctly, what's up with ping and ssh? 

Thanks for your help. 

gaebriel

---

### Post by dcstar on 2009-03-30
> **gaebriel said:**
> Hi, I'm experiencing an interesting error when trying to ping or SSH to a host by using its FQDN. The problem is most annoying since I have multiple domains with similar hostnames so when I try to ssh to them, I need to make sure I'm hitting the right one. For example, I have mail servers at each of these domains I support called mx1.domain1.com, mx1.domain2.com, mx1.domain3.com... 
......

AFAIK if you server has multiple identities, then you have to tell it those identities.

What is in you hosts file?

---

### Post by gaebriel on 2009-03-31
Thanks for the reply. It's not that I have multiple identities for a single server, I'm just trying to resolve unique fully qualified domain names for multiple hosts that happen to have the same host name, but different domain names. 

My /etc/hosts file contains only two entries and they're for my local machine. If I add the FQDNs for each host in question into my /etc/hosts file, I can ping and ssh to them. I'm not about to add 5-10 server addresses for each of these domains into a hosts file that I have to maintain across 10 servers/workstations and update anytime something changes. I want to use DNS, which is clearly working correctly when queried by 'host' or 'dig' commands. 

Sure, I could implement a system that replicates my /etc/hosts file across multiple boxes, but I really don't want to. :)

---

### Post by dcstar on 2009-03-31
> **gaebriel said:**
> Thanks for the reply. It's not that I have multiple identities for a single server
.......

Then why do you have multiple search entries in the resolv.conf?

That is for the **local** machine only.

---

### Post by hyper_ch on 2009-04-01
do you have a nameserver running at 10.1.1.2?

---

### Post by gaebriel on 2009-04-03
I manage about 10 client offices, each with their own domain name and servers. They have some similar infrastructure, like an antivirus server (av1.domain-name1.local, av1.domain-name2.local...), a mail server (mx1.domain-name1.local, mx1.domain-name2.local...), a backup server (archive1.domain-name1.local, archive1.domain-name2.local...), and some servers that are unique for each site because I inherited some of these networks with their own naming scheme and haven't gotten around to changing them. 

I have multiple entries in my search field because it's nice to just specify the host name for those unique servers instead of typing the whole fqdn. Several sites originally an acronym for the organization included as part of the name, so there are servers with hostnames like: dom1-dc, dom1-pc01, dom1-pc02, dom2-svr, dom2-mail and so on and so forth. Since those hostnames are unique among all the domains I manage, if I append the "domain-name1.local, domain-name2.local..." entries in my search string, I can hit any of those servers without having to type the whole fqdn. 

That part works great. It's when the servers have the same host name and different fqdn that the ping and ssh commands fail to find the servers. I've tried eliminating all but one search suffix, and then I can reach any of the servers by their FQDN, but my ability to reach the servers that already have unique host names without having to type their FQDN is lost. 

This is a little thing, for sure. And I'm not so lazy that can't just always type the fqdns of every server, every time. I'd prefer not to though, and there's no reason I should have to. Even windows boxes can have multiple search suffixes appended to a client's DNS queries and it since the host and dig commands work, there's clearly something broken with respect to the way ping and ssh resolve hostnames/fqdns to IPs. I don't like working with a system I know is broken. :)

---

### Post by gaebriel on 2009-04-03
Perfectly valid question, but yes I have a nameserver running at 10.1.1.2. And running "dig @10.1.1.2 mx1.domain-name1.local" or "dig @10.1.1.2 mx1.domain-name2.local" or "dig @10.1.1.2 dom4-mx1" resolves the correct IP address. But, while running "ssh [email]me@mx1.domain-name1.local[/email]" works, and "ssh me@dom4-mx1" works, running "ssh [email]me@mx1.domain-name2.local[/email]" fails.

---

### Post by hyper_ch on 2009-04-04
hmm.... what ip address that does that local domain resolve to? Maybe it's wrong in your dns cache on that machine?

---

### Post by gaebriel on 2009-04-04
Until your post made me research this further, the only DNS caching service I knew of for linux was nscd and that's neither running nor even installed. I was sure there wasn't anything incorrect in the DNS cache itself because the IPs are all unique and have been since their inception, and the DNS zones in question haven't changed in months and this happens on all ubuntu workstations/servers in my office, and a reboot of the boxes didn't help the situation. With no conflicting entries ever existing in the DNS servers, how could the DNS cache even be an issue? 

Your question made me wonder about what DNS or networking services are running in ubuntu trying to make life simpler somehow for people that don't know what they're doing and in the process break the system for those of us that love fine-tuning our systems. A necessary evil in my opinion. Linux needs to be easy to use for new people to try it out and use it efficiently, but there should be a program available to turn off all the child-proofing mechanisms a distribution includes so that real Linux admins can obtain the behavior they expect when they configure something. But I digress...

I have windows boxes running in my office network (10.1.1.0/24) as VMs and this DNS resolution process works. More importantly, I verified this morning that my openfiler NAS, a Fedora 10 VM, and some CentOS 5.2 hosts on my network can use 'host', 'dig', 'ping', and 'ssh' and resolve any hostname or FQDN properly. (i.e. ssh or ping to mx1.domain-name1.local, mx1.domain-name2.local, or dom2server1 without a problem). The problem described in this thread is unique to every Ubuntu box on my lan. I'm running Ubuntu 8.04.2, and Ubuntu 8.10. 

There are only a few packages I'm aware of in ubuntu that are involved with name resolution or network auto-configuration: dnsutils, resolvconf, network manager perhaps, and avahi. The dnsutils (dig, nslookup, nsupdate) were all working like they should. The resolvconf package wasn't installed. The Network-Manager service has bitten me before when I try to use a laptop wireless connection and a LAN connection simultaneously, or when I define a static IP address on a box and the network connection drops and then replaces my config with an attempted DHCP address again. So I killed the Network-Manager service and the problem persisted. 

That left me with the avahi-daemon. I didn't know exactly what it did before this morning; I just had some vague recollection associating it with bonjour or zeroconf or something or other. Reading the man page for avahi-daemon, I found it uses something called the mDNS record cache, and that was enough for me. Turning off the avahi-daemon, my ubuntu box works like it should now. Thanks for making me reconsider the DNS cache issue and I'm going to research this dastardly service to see if it does anything actually worthwhile. Until then, I'm taking it out of the system startup.

---

### Post by TWGTech on 2009-06-04
I see that this is an old post, but I too was having the same issue. Thanks for all the legwork on this. I stopped avahi-daemon and was able to resolve my search issues.

I am running into another issue related to this that perhaps you have also had to work out. If this post is too old for this, or it's too off-topic, let me know and I'll be glad to repost.

Whenever I make a change in the Network applet (Jaunty w/ Gnome), it not only doesn't allow me to modify the Hosts entries (selecting an entry and then Properties closes the window), but it also replaces the hostname with the FQDN in /etc/hosts, causing my sudo to complain.

Example - 
Current hosts entries - 
127.0.0.1       computername.domain.name localhost.localdomain localhost
xx.xxx.xxx.xxx    computername.domain.name computername

I enter the Network applet, make a change such as adding a search domain, and select Close.

New hosts entries - 
127.0.0.1       computername.domain.name localhost.localdomain localhost
xx.xxx.xxx.xxx    computername.domain.name computername.domain.name

Enter a sudo command in Terminal.
sudo: unable to resolve host computername

This only happens when making a change. If I enter the applet and do not change anything, the hosts files stays the same. I am unable to change anything in the Hosts tab. As stated prior, any attempt closes the window.

The order of the entries in hosts does not matter, either. I have to manually modify the hosts file in order to restore functionality.

---


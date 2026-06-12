---
title: "any easier gamblng blocks for ubuntu"
date: 2023-08-15
forum: Gaming &amp; Leisure
---

### Post by smallville1979 on 2023-08-15
I am poor at programming! 
I quit gambling. is there anymore easy to install blocks to block non gamstop casinos and all gambling sites. 
I am not confident I have enough today. 
struggling to get stuff installed on ubuntu 22.04. 

appreciate any help and ideas please?

---

### Post by Frogs Hair on 2023-08-15
Hello, smallville 1979, 

I'm not sure what you mean by easier. Please describe what you are already doing. There are plenty of site blocking extensions most any web browser, but you have to enter the url of the sites you wish to block.

---

### Post by #&amp;thj^% on 2023-08-15
> **smallville1979 said:**
> I am poor at programming! 
I quit gambling. is there anymore easy to install blocks to block non gamstop casinos and all gambling sites. 
I am not confident I have enough today. 
struggling to get stuff installed on ubuntu 22.04. 

appreciate any help and ideas please?

This one has a decent review and it installs with a .deb: [https://betblocker.org/](https://betblocker.org/)
Good Luck with your new found direction though.

---

### Post by mIk3_08 on 2023-08-17
> **smallville1979 said:**
> I am poor at programming! 
I quit gambling. is there anymore easy to install blocks to block non gamstop casinos and all gambling sites. 

Try this Gump  is a free and open-source content blocker that can be installed on  Linux. It can be used to block gambling websites and apps, as well as  other types of websites.

[RBlock ]("http://www.hrblock.com")is  another free and open-source content blocker that can be installed on  Linux. It is similar to Gump, but it has a few additional features, such  as the ability to block ads and trackers.

Pi-hole  is a free and open-source DNS sinkhole that can be installed on a  Raspberry Pi or other Linux device. It can be used to block gambling  websites and apps by redirecting their traffic to a black hole.

[OpenDNS]("http://www.opendns.com")  Family Shield is a free DNS service that can be used to block gambling  websites and apps. It can be configured on any device that uses DNS,  such as a computer, phone, or router.

[Norton ConnectSafe]("https://support.norton.com/")  is a paid DNS service that can be used to block gambling websites and  apps. It also has a number of other features, such as malware protection  and parental controls.

These  are just a few of the many easy to install blocks that can be used to  block non-GamStop casinos and all gambling sites for Linux. When  choosing a blocking software, it is important to consider your needs and  budget. You should also make sure that the software is compatible with  your devices. Regards and cheers

---

### Post by TheFu on 2023-08-17
+1 for setting up a **pi-hole**.  I run 2 inside Ubuntu LXD containers - primary and backup.  Keeps the pihole stuff separate from the main OS, but it is still fast.  There are pihole blocklists for all sorts of things.  Let me look for gambling stuff.  [https://avoidthehack.com/best-pihole-blocklists](https://avoidthehack.com/best-pihole-blocklists)  Pi-hole became popular for running on raspberry pi computers, but that isn't the only way to run it.  If you have an old raspberry pi v2 that isn't being used anymore a pi-hole would be a good use for it.

[https://discourse.pi-hole.net/t/is-there-a-library-for-pihole-for-blocking-gambling-ads/55991](https://discourse.pi-hole.net/t/is-there-a-library-for-pihole-for-blocking-gambling-ads/55991) points out that some gambling websites use straight IP addresses, not DNS, for their servers.  That means a pi-hole doing DNS filtering won't be useful. You'll need to make a list of IPs or subnets and use a real firewall to block those as you see them.

For most people, using OpenDNS, which is owned by Cisco (just so you know), would be one of the easiest answers. Of course, letting a corporation like Cisco see all the DNS queries from your systems might not be the best idea.  Only you can answer that for your privacy concerns, if any.  As a gambler, I suspect privacy wasn't the most important thing. That will probably follow you as long as you retain any old email accounts or the same accounts on social networking sites.  I don't see any advertisements for gambling, because that doesn't interest me and I've never actually gambled IRL or online.  But you are probably very familiar with the way advertising is targeted once any interest is shown in a topic with massive advertising budgets.  It is hard for everyone, not just average people, to have some level of privacy online.  

There is a per-user firewall of Linux too, **OpenSnitch**.  I think it is too much hassle, but know a few people running it who say it is a hassle for about a week as they mark things to be allowed and things to be blocked. Eventually, the hassles become less and less, until they have a great setup. [https://itsfoss.com/opensnitch-firewall-linux/](https://itsfoss.com/opensnitch-firewall-linux/) explains. I think the install and setup are a little nerdy, but most things are addressed via a GUI, so it isn't THAT bad.

I have my own addictions and advertisers are ruthless with those, if I allow any advertising at all.  I strive to block most of it though firewall rules and the pihole.  Some parts of the internet don't work for me, unless I relax the blocking.

---

### Post by smallville1979 on 2023-10-15
I was using OPENDNS is it quickly deleted as is all browser extension blocks it slows me down a little. gamban work wont. is there anything paid to block it for good? 
I gambled every penny need a loan now.

---


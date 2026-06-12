---
title: "Ubuntu / Kubuntu Frequent internet disconnect"
date: 2007-08-18
forum: Desktop Environments
---

### Post by gtdaqua on 2007-08-18
Hi everyone!

I am having a strange problem - i am an IT savvy myself but I am stumped here. 

I installed Kubuntu 64bit like a month ago on an DELL Optiplex AMD64. Was surfing internet in full speed. Ran apt-get install/upgrade - no problems. 

Recently, i got frequently disconnected from internet. LAN worked superfast. It always is. 

Internet would just drop if i dont browse for some time. Then it would come back up after several time out issues!! 

NIC cant be a problem because I am typing this post from a VM on another server in a LAN! I can get instant internet connections on any VM anytime. 

But on my desktop i get disconnected every now and then!! Tried configuring OpenDNS, disabled IPv6, but no go!!

So to keep continous internet, i have to leave a terminal pinging google.com always and browse in the background so that I dont lose the connection! Connected to a Gb switch and had these problems. Connected back to a 100Mbps switch - still the same issue.

My Network config:

Desktop IP: 192.168.6.101/24
Gateway: 192.168.6.1 (Dell L3 switch)
ADSL Router: 192.168.6.253
DNS: 192.168.6.9 (all other servers are using this server) and 208.67.222.22

Same configuration for VMs (Win Server 2003) but they dont have any problems!! 

Can someone help me? I love kubuntu - its just the internet which is being a pain now!!

Thanks!

---

### Post by zensmile on 2008-04-21
I am having very similar problems with my install of 8.04 (PC (Intel x86) desktop CD). Everything will be great, then the internet drops out and doesn't return. I have tried logging in and out, restarting, moving back and forth from manual to roaming, nothing seems to work. It just drops off and comes back whenever. I am *not* as tech savvy as you are, but I also tried Open DNS. It didn't work. I tried both a supported wifi USB adapter and using the hardwired ethernet port--both methods still get intermittent internet access. It isn't the router or my cable modem, all of the other computers connect and maintain a connection without a problem. I also ran the package manger to make sure that the system was up-to-date. So I am a little discouraged.

---


---
title: "Problem with pinging after resolving a host on a local machine"
date: 2008-01-26
forum: Desktop Environments
---

### Post by ismarj on 2008-01-26
Hallo everybody,

I'm having problem pinging my local ethernet interface. I have installed Ubuntu 7.10.
What I want to do is to run an application on my machine and to make it accesible via hostname. So I've made changes in bind configuration (added zone in /etc/bind/named.conf.local) which connect the host name with IP address of my Ethernet interface. 
The application I'm running consists of 4 relatively isolated parts which communicate using hostnames which are though dns converted into IP addresses. In my case, all application run on the same machine, so all host names are converted into the IP address of my ethernet port (192.168.0.1). Every application listens different port. Original settings for application use localhost address (127.0.0.1) and everithing works fine. But I need access to the applications over network, so localhost address is not good for me.
This is what happens when I make the changes and start using 192.168.0.1: everithing looks fine in the configuration, but my applications start very slow (in the startup process application have to communicate). So everithing works, but very slow. Clients that are connecting to the application work very slow because delay. Client application which runs on ubuntu on the other computer also work but slow. A windows application, on the other side, works fine?!
I have tried pinging the hostnames, it is obvious that dns does the resolving, but i get icmp replies with significant delay. By this I mean time between echo request is very long (about 15s), echo reply is normal (few miliseconds).
Anybody expirienced similar problem.
Thanks in advance.

---

### Post by MasterJS on 2008-01-26
Have you checked your connections? If they are wired connections, it's possible something is loose. If it is a wireless connection, then you need to check that computers are place at the right locations for optimum speed.

---

### Post by dcstar on 2008-01-26
> **ismarj said:**
> Hallo everybody,

I'm having problem pinging my local ethernet interface. I have installed Ubuntu 7.10.
What I want to do is to run an application on my machine and to make it accesible via hostname. So I've made changes in bind configuration (added zone in /etc/bind/named.conf.local) which connect the host name with IP address of my Ethernet interface. 
The application I'm running consists of 4 relatively isolated parts which communicate using hostnames which are though dns converted into IP addresses. In my case, all application run on the same machine, so all host names are converted into the IP address of my ethernet port (192.168.0.1). Every application listens different port. Original settings for application use localhost address (127.0.0.1) and everithing works fine. But I need access to the applications over network, so localhost address is not good for me.
This is what happens when I make the changes and start using 192.168.0.1: everithing looks fine in the configuration, but my applications start very slow (in the startup process application have to communicate). So everithing works, but very slow. Clients that are connecting to the application work very slow because delay. Client application which runs on ubuntu on the other computer also work but slow. A windows application, on the other side, works fine?!
I have tried pinging the hostnames, it is obvious that dns does the resolving, but i get icmp replies with significant delay. By this I mean time between echo request is very long (about 15s), echo reply is normal (few miliseconds).
Anybody expirienced similar problem.
Thanks in advance.

Check you /etc/hosts file, and the order in which your local name resolution is set.

---


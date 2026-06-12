---
title: "Networking Issue"
date: 2009-06-03
forum: General Help
---

### Post by Coding Monkey on 2009-06-03
Hi All

I have what seems like a networking issue, and I am getting pretty fed up trying to resolve it.  I am using Ubuntu 8.10.  After start up, I can view websites for a while, but after a few minutes I can't access websites anymore.  I found that running ```
sudo /etc/init.d/networking restart
``` fixes the problem... for a few minutes.  Does anyone have an idea what could be causing this?  Thanks a lot.

By the way, I can still access PC's on the local LAN.  I originally thought that this might be a DNS issue, but I can't access websites using their IP addresses either.  I tried pinging the forums (91.189.94.12), to no avail.  I tried searching the forums, but finding a solution is kind of hard when you are unsure what the problem is.

---

### Post by dcstar on 2009-06-03
> **Coding Monkey said:**
> Hi All

I have what seems like a networking issue, and I am getting pretty fed up trying to resolve it.  I am using Ubuntu 8.10.  After start up, I can view websites for a while, but after a few minutes I can't access websites anymore.  I found that running ```
sudo /etc/init.d/networking restart
``` fixes the problem... for a few minutes.  Does anyone have an idea what could be causing this?  Thanks a lot.

By the way, I can still access PC's on the local LAN.  I originally thought that this might be a DNS issue, but I can't access websites using their IP addresses either.  I tried pinging the forums (91.189.94.12), to no avail.  I tried searching the forums, but finding a solution is kind of hard when you are unsure what the problem is.

You need to look at the log files:

```
System-Administration-Log File Viewer
```

---

### Post by Coding Monkey on 2009-06-03
Hi David

Thank you for your reply.  I had a look at the system log, and it seems like my machine thinks that it should be using a dynamic address, thus it gets renewed every few minutes.  I find that very strange.  

My interfaces file looks like this.  (The static address is for work, and at home I just comment that out and use the dynamic one)  My static address, netmask, gateway, and dns-nameservers have valid values, I just changed them before posting it online.

```
auto lo
iface lo inet loopback

auto eth0

#iface eth0 inet dhcp

iface eth0 inet static
address Address
netmask Netmask
gateway Gateway
dns-nameservers DNS Server
```

Does anything look wrong in there?  Once again, thanks for your help.  I am pretty clueless when it comes to networking in Ubuntu.

---

### Post by Coding Monkey on 2009-06-03
Anyone?

---

### Post by Coding Monkey on 2009-06-03
Bump?  (I thought I'd try my luck one last time.)

---


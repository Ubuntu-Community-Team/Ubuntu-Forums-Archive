---
title: "Abyss ?where does this come from?"
date: 2009-01-12
forum: General Help
---

### Post by briandu on 2009-01-12
I have via nmap reporting abyss 9999. I see abyss is a mini webserver.

The PC is a std Ubuntu 8.10 with wine and WOW and OpenOffice.

Anyone know where this abyss is coming from - the HP print server?:confused:

Any ideas?

TIA

---

### Post by albinootje on 2009-01-12
> **briandu said:**
> I have via nmap reporting abyss 9999.

Try : 
```

netstat -tan | grep 9999
netstat -ta

```
And compare those two, to find a name.

---

### Post by hangfire on 2009-01-12
> **briandu said:**
> I have via nmap reporting abyss 9999. I see abyss is a mini webserver.

The PC is a std Ubuntu 8.10 with wine and WOW and OpenOffice.

Anyone know where this abyss is coming from - the HP print server?:confused:

Any ideas?

TIA

Use lsof to find out what process is holding that port open

```
sudo apt-get install lsof
lsof | grep 9999
*someprogname blah blah blah*
# Find out information about program *someprogname*
locate *someprogname*
sudo apt-get install apt-file
apt-file search *someprogname*
```


-HF

---

### Post by briandu on 2009-01-12
when I run netstat -tan | grep 9999 I get nothing

when I run netstat -tan I get a list of transactions to several IP addresses. I can trace them all (well not all info) but cannot resolve these:

[IMG]file:///tmp/moz-screenshot.jpg[/IMG]traceroute to 213.123.85.201 (213.123.85.201), 30 hops max, 40 byte packets
 1  api.home (192.168.1.254)  11.428 ms  10.816 ms  10.154 ms
 2  esr1.kingston4.broadband.bt.net (217.47.46.140)  24.782 ms * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * 217.41.171.69 (217.41.171.69)  22.783 ms  20.024 ms
 8  213.123.85.2 (213.123.85.2)  23.053 ms  22.884 ms  22.873 ms
 9  213.123.85.201 (213.123.85.201)  21.858 ms  20.513 ms  21.193 ms
xxxxxx@LinuxQ6WkStn:~$ sudo tracert 216.73.84.9
traceroute to 216.73.84.9 (216.73.84.9), 30 hops max, 40 byte packets
 1  api.home (192.168.1.254)  10.677 ms  10.069 ms  9.395 ms
 2  esr1.kingston4.broadband.bt.net (217.47.46.140)  24.910 ms * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * 217.41.171.62 (217.41.171.62)  22.070 ms  22.834 ms
 8  217.47.46.82 (217.47.46.82)  54.890 ms  56.093 ms  57.311 ms
 9  194.72.3.121 (194.72.3.121)  56.575 ms  60.211 ms  205.718 ms
10  core2-pos0-8-0-1.ilford.ukcore.bt.net (62.6.201.125)  54.924 ms  52.940 ms  52.932 ms
11  core2-pos14-1.telehouse.ukcore.bt.net (195.99.125.229)  27.073 ms  39.923 ms  36.166 ms
12  uk-bs1-p.doubleclick.net (195.66.225.45)  23.847 ms  23.834 ms  25.263 ms
13  216.73.84.9 (216.73.84.9)  21.416 ms  21.664 ms  23.170 ms
xxxxxx@LinuxQ6WkStn:~$ sudo tracert 217.41.217.205
traceroute to 217.41.217.205 (217.41.217.205), 30 hops max, 40 byte packets
 1  api.home (192.168.1.254)  68.071 ms  67.385 ms  66.712 ms
 2  esr1.kingston4.broadband.bt.net (217.47.46.140)  24.883 ms * *
 3  * * *
 4  * * *
 5  * * *
 6  * 217.41.171.66 (217.41.171.66)  26.126 ms  22.154 ms
 7  217.41.171.78 (217.41.171.78)  29.862 ms *  22.736 ms
 8  * * 217.41.171.69 (217.41.171.69)  21.843 ms
 9  213.123.85.2 (213.123.85.2)  20.974 ms  22.199 ms  21.843 ms
10  217.41.217.205 (217.41.217.205)  21.654 ms  23.831 ms  19.948 ms


Is this weird or what?
 217.41.217.205
213.123.85.201 are BT - maybe this is Phorm????

---

### Post by albinootje on 2009-01-12
> **briandu said:**
> when I run netstat -tan | grep 9999 I get nothing

when I run netstat -tan I get a list of transactions to several IP addresses. 

That's a little bit weird.
```

$ host 213.123.85.201
Host 201.85.123.213.in-addr.arpa. not found: 3(NXDOMAIN)

```

Are you not behind a DSL-router or Cable-modem which is in bridged mode, and using a firewall ?

Are you using Skype or p2p software ? 
Skype makes "decentralized" connections to other desktop machines of other computer users.

lsof is indeed a good way to search for what is using port 9999 but it can generate a lot of output.
Can you try :
```

lsof|grep 9999

```
anyway ?

---

### Post by briandu on 2009-01-12
Unfortunately I cannot check now. I will use lsoff next opportunity and check it out.

Thx

---

### Post by cariboo on 2009-01-12
Can you connect to it in Firefox


[http://abyss_server:9999](http://abyss_server:9999)

Where abyss_server is the server it is on.

Have a look at this [article]("http://www.securiteam.com/securitynews/5LP0E1F95K.html").

Jim

---


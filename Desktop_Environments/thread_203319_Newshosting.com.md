---
title: "Newshosting.com"
date: 2006-06-25
forum: Desktop Environments
---

### Post by shaun_ on 2006-06-25
For some reason ever since the recent round of updates on dapper newshosting.com has been unreacahble for me.

I was wondering if there was a hosts file like in windows which blocked sites.

The reason i ask is both my news reader clients seem unable  to connect to the newshosting domains without getting either no response or they display a negative transfer rate i.e -700KB/s.

I can ping unlimited.newshosting.com and get an average of 107ms which is acceptable as i am in the UK and the servers are in the US.

However pinging [www.newshosting.com](www.newshosting.com) yeilds complete packet loss.

Since this machine dual boots with windows I rebooted into XP and tried the servers and website for newshosting and had no problems reaching the site or downloading from the server. This leaves me with the impression that the domain is being blocked somewhere.

Any other ideas or clues as to where to start looking to fix this?

EDIT* pinging from windows gives complete packet loss too so im guessing there blocking ICMP ping requests. However visiting the [www.newshosting](www.newshosting) site with firefox yeilds no response in ubuntu but in windows it comes up straight away. This problem is getting stranger and stranger.

---

### Post by bohboh on 2006-06-25
Try

/etc/hosts

---

### Post by shaun_ on 2006-06-26
Thanks. Had a look there and theres nothing which interfere with the newshosting site that i can see.

I tried adding a free usenet server to klibido and seeing if i could pull a list of groups from that, and it worked great. However newshosting fails miserably.

This has really got me stumped now. Might be a need for me to switch providers.

---

### Post by bohboh on 2006-06-26
Who is your provider?

---

### Post by shaun_ on 2006-06-26
Newshosting is my usenet provider.

Its definately not related to my ISP as I can access and and retrieve information from my windows account. It just doesnt work under ubuntu any more. Newshosting have probably done something strange in the last few days which is confusing something somewhere.

---

### Post by bohboh on 2006-06-26
What happens when you run this?

[http://www.newshosting.com/support/util/traceroute/](http://www.newshosting.com/support/util/traceroute/)

---

### Post by shaun_ on 2006-06-26
Works great in windows and completes the reverse traceroute.

Does not even bring up the newshosting site in ubuntu.

I did try a trace route/path in both ubuntu and windows and both completed without issues in the CLI.

```

shaun@PC2:~$ tracepath  unlimited.newshosting.com/119
 1:  192.168.1.3 (192.168.1.3)                              0.394ms pmtu 1492
 1:  192.168.1.1 (192.168.1.1)                              1.695ms
 2:  host-83-146-18-122.bulldogdsl.com (83.146.18.122)    asymm  3  46.635ms
 3:  ge-1-0-0.33.cht-cor-001.bddsl.net (83.146.22.126)    asymm  4  51.932ms
 4:  so-0-0-0.0.thn-cor-001.bddsl.net (83.146.19.153)     asymm  5  49.386ms
 5:  cr02.ldn01.pccwbtn.net (195.66.224.167)               50.060ms
 6:  newshosting.ge2-2.br02.ash01.pccwbtn.net (63.218.94.110) asymm 10 131.307ms
 7:  no reply

```

This being the newserver I need to connect to to retrieve any binaries.

Hoever for the website [www.newshosting.com](www.newshosting.com)

```

shaun@PC2:~$ tracepath  newshosting.com
 1:  192.168.1.3 (192.168.1.3)                              0.426ms pmtu 1500
 1:  192.168.1.1 (192.168.1.1)                              1.033ms
 2:  192.168.1.1 (192.168.1.1)                            asymm  1   7.556ms pmtu 1492
 3:  ge-0-0-0.30.cht-cor-001.bddsl.net (83.146.22.30)     asymm  4  58.027ms
 4:  ge-0-0-0.dcr1.lnd.cw.net (195.10.12.1)               asymm  5  49.454ms
 5:  195.2.9.13 (195.2.9.13)                              asymm  6  50.062ms
 6:  so-0-0-0-dcr1.nyk.cw.net (195.2.10.109)              122.713ms
 7:  so-7-0-0-dcr1.was.cw.net (195.2.3.1)                 127.328ms
 8:  195.2.0.218 (195.2.0.218)                            128.938ms
 9:  10ge5.j3.iad.scnet.net (206.223.115.57)              129.514ms
10:  ge2-7.b2.iad.scnet.net (66.225.244.210)              asymm 11 130.751ms
11:  ge3-0-1.3939.j2.ord.scnet.net (205.234.205.77)       asymm 12 158.563ms
12:  so2-1-0.j1.ord.scnet.net (205.234.158.81)            asymm 13 157.851ms
13:  unknown.ord.scnet.net (205.234.205.118)              155.890ms
14:  no reply

```

This happens in both windows and linux but the difference being I can still get the site up in Firefox under windows.

Its of no matter now anyway as I have cancelled my newshosting account and switched to giganews which is working fine. Bit of a shame as Newshosting was better value for money for me.

---


---
title: "internet slow (across all browser + command line tools)"
date: 2009-04-10
forum: General Help
---

### Post by bricedebrignaisplage on 2009-04-10
Hi

My internet connection became very slow suddenly. When using Firefox and Konqueror, when downloading packages with synaptic or apt-get, when doing ssh or ftp connections, even pingging google (4.5s)...

I did a test at speedtest.net and it reports a 1.1MB/s download speed and a ping of 4.5s.

I am using Hardy + KDE3.5 (Kubuntu 8.04).

Rebooting does not help (btw I cannot logout, but I don't think it's related, is it?). The only thing that helps is to boot a different OS (debian). When I come back to my main Hardy it is fast as usual, for a while. After some time (I don't know exactly how long, but less than 12 hours) it slows down again.

Anybody has a clue to what is happening?

Regards
Brice

---

### Post by _khAttAm_ on 2009-04-10
install nethogs and try running 
sudo nethogs
to see if anything else is using your internet.

---

### Post by bricedebrignaisplage on 2009-04-11
Thank you _khAttAm_ for your answer. nethogs is a neat program, I wonder how come I've never heard of it before. Thanks for that.

There was 2 instances of sshd running, downloading at 30kb/s (total) from my computer. Can it be that such a small upload speed kills my bandwith? I'll investigate that next time I'm experiencing a slow down.

tcpdump shows weird entries (see below) when all internet activity is off (nethogs shows nothing). maxonline.com.sg is my ISP... Is that normal?




23:04:30.187660 arp who-has cm17.omega182.maxonline.com.sg tell cm1.omega176.maxonline.com.sg
23:04:30.188480 arp who-has cm17.omega182.maxonline.com.sg tell cm1.omega176.maxonline.com.sg
23:04:30.188902 IP cm89.zeta82.maxonline.com.sg.36965 > dns2.maxonline.com.sg.domain: 8784+ PTR? 17.182.186.218.in-addr.arpa. (45)
23:04:30.199408 IP dns2.maxonline.com.sg.domain > cm89.zeta82.maxonline.com.sg.36965: 8784* 1/3/3 (194)
23:04:30.199705 IP cm89.zeta82.maxonline.com.sg.55859 > dns2.maxonline.com.sg.domain: 25626+ PTR? 1.176.186.218.in-addr.arpa. (44)
23:04:30.227026 IP dns2.maxonline.com.sg.domain > cm89.zeta82.maxonline.com.sg.55859: 25626* 1/3/3 (192)
23:04:30.227639 IP cm89.zeta82.maxonline.com.sg.34011 > dns2.maxonline.com.sg.domain: 59542+ PTR? 48.1.156.202.in-addr.arpa. (43)
23:04:30.265865 IP dns2.maxonline.com.sg.domain > cm89.zeta82.maxonline.com.sg.34011: 59542* 1/3/3 (178)
23:04:30.266158 IP cm89.zeta82.maxonline.com.sg.41512 > dns2.maxonline.com.sg.domain: 9820+ PTR? 89.82.87.116.in-addr.arpa. (43)
23:04:30.315034 IP dns2.maxonline.com.sg.domain > cm89.zeta82.maxonline.com.sg.41512: 9820* 1/3/3 (190)
23:04:35.186067 arp who-has cm1.zeta82.maxonline.com.sg tell cm89.zeta82.maxonline.com.sg
23:04:35.186375 IP cm89.zeta82.maxonline.com.sg.41640 > dns2.maxonline.com.sg.domain: 4263+ PTR? 1.82.87.116.in-addr.arpa. (42)
23:04:35.195160 arp reply cm1.zeta82.maxonline.com.sg is-at 00:30:b8:c1:18:10 (oui Unknown)
23:04:35.196421 IP dns2.maxonline.com.sg.domain > cm89.zeta82.maxonline.com.sg.41640: 4263* 1/3/3 PTR[|domain]

---


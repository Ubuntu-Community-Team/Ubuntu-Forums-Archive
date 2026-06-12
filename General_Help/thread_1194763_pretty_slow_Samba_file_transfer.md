---
title: "pretty slow Samba file transfer"
date: 2009-06-23
forum: General Help
---

### Post by raghu1111 on 2009-06-23
I mounted a samba volume on XP. XP and Ubuntu are connected over 100Mbps ethernet (router).

I am writing a 4GB file from XP to Ubuntu and the transfer is extremely slow : only around 1-1.5 MB/s. 

This is not a network or disk issue since at the same time this transfer is gonig on, I can scp the same file from XP to Ubuntu at 3-4 times faster (around 6MB/s). 

What could be wrong? Even for this slow transfer, smbd seems to be taking quite a bit CPU (more than sshd for the transfer rate).

Reading from Ubuntu on this Samba volume is not much faster. only above 3MB/s.

It is pretty surprising. Please let me know if you need any more info about the problem.

Regd config, only changes I made to smb.conf are for adding shares.

Thanks,
Raghu.

---

### Post by raghu1111 on 2009-06-24
Sample tcpdump for such a connection: It transfers 1KB at a time. Unfortunately it takes around 0.3-0.5 milliseconds :
```

18:50:57.948157 IP 192.168.0.100.4366 > 192.168.0.104.445: P 2184:3276(1092) ack 103 win 64719
18:50:57.948374 IP 192.168.0.104.445 > 192.168.0.100.4366: P 103:154(51) ack 3276 win 65535
18:50:57.948897 IP 192.168.0.100.4366 > 192.168.0.104.445: P 3276:4368(1092) ack 154 win 64668
18:50:57.949074 IP 192.168.0.104.445 > 192.168.0.100.4366: P 154:205(51) ack 4368 win 65535
18:50:57.949615 IP 192.168.0.100.4366 > 192.168.0.104.445: P 4368:5460(1092) ack 205 win 64617
18:50:57.949831 IP 192.168.0.104.445 > 192.168.0.100.4366: P 205:256(51) ack 5460 win 65535
18:50:57.950437 IP 192.168.0.100.4366 > 192.168.0.104.445: P 5460:6552(1092) ack 256 win 64566
18:50:57.950649 IP 192.168.0.104.445 > 192.168.0.100.4366: P 256:307(51) ack 6552 win 65535
18:50:57.951152 IP 192.168.0.100.4366 > 192.168.0.104.445: P 6552:7644(1092) ack 307 win 64515
18:50:57.951389 IP 192.168.0.104.445 > 192.168.0.100.4366: P 307:358(51) ack 7644 win 65535
18:50:57.951911 IP 192.168.0.100.4366 > 192.168.0.104.445: P 7644:8736(1092) ack 358 win 64464
18:50:57.952090 IP 192.168.0.104.445 > 192.168.0.100.4366: P 358:409(51) ack 8736 win 65535
18:50:57.952608 IP 192.168.0.100.4366 > 192.168.0.104.445: P 8736:9828(1092) ack 409 win 64413
18:50:57.952801 IP 192.168.0.104.445 > 192.168.0.100.4366: P 409:460(51) ack 9828 win 65535
18:50:57.953299 IP 192.168.0.100.4366 > 192.168.0.104.445: P 9828:10920(1092) ack 460 win 64362
18:50:57.953489 IP 192.168.0.104.445 > 192.168.0.100.4366: P 460:511(51) ack 10920 win 65535
18:50:57.954038 IP 192.168.0.100.4366 > 192.168.0.104.445: P 10920:12012(1092) ack 511 win 64311
18:50:57.954286 IP 192.168.0.104.445 > 192.168.0.100.4366: P 511:562(51) ack 12012 win 65535
18:50:57.954794 IP 192.168.0.100.4366 > 192.168.0.104.445: P 12012:13104(1092) ack 562 win 65535
18:50:57.954982 IP 192.168.0.104.445 > 192.168.0.100.4366: P 562:613(51) ack 13104 win 65535
18:50:57.955531 IP 192.168.0.100.4366 > 192.168.0.104.445: P 13104:14196(1092) ack 613 win 65484
18:50:57.955702 IP 192.168.0.104.445 > 192.168.0.100.4366: P 613:664(51) ack 14196 win 65535
18:50:57.956207 IP 192.168.0.100.4366 > 192.168.0.104.445: P 14196:15288(1092) ack 664 win 65433
18:50:57.956497 IP 192.168.0.104.445 > 192.168.0.100.4366: P 664:715(51) ack 15288 win 65535
18:50:57.956984 IP 192.168.0.100.4366 > 192.168.0.104.445: P 15288:16380(1092) ack 715 win 65382
18:50:57.957213 IP 192.168.0.104.445 > 192.168.0.100.4366: P 715:766(51) ack 16380 win 65535
18:50:57.957765 IP 192.168.0.100.4366 > 192.168.0.104.445: P 16380:17472(1092) ack 766 win 65331
18:50:57.957963 IP 192.168.0.104.445 > 192.168.0.100.4366: P 766:817(51) ack 17472 win 65535
18:50:57.958462 IP 192.168.0.100.4366 > 192.168.0.104.445: P 17472:18564(1092) ack 817 win 65280
18:50:57.958658 IP 192.168.0.104.445 > 192.168.0.100.4366: P 817:868(51) ack 18564 win 65535
18:50:57.959198 IP 192.168.0.100.4366 > 192.168.0.104.445: P 18564:19656(1092) ack 868 win 65229
18:50:57.959367 IP 192.168.0.104.445 > 192.168.0.100.4366: P 868:919(51) ack 19656 win 65535
18:50:57.959880 IP 192.168.0.100.4366 > 192.168.0.104.445: P 19656:20748(1092) ack 919 win 65178

```

---

### Post by dcstar on 2009-06-24
> **raghu1111 said:**
> I mounted a samba volume on XP. XP and Ubuntu are connected over 100Mbps ethernet (router).

I am writing a 4GB file from XP to Ubuntu and the transfer is extremely slow : only around 1-1.5 MB/s. 
.........
It is pretty surprising. Please let me know if you need any more info about the problem.

Regd config, only changes I made to smb.conf are for adding shares.

Thanks,
Raghu.

[http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html)

[http://oreilly.com/catalog/samba/chapter/book/appb_02.html](http://oreilly.com/catalog/samba/chapter/book/appb_02.html)

---

### Post by raghu1111 on 2009-06-24
Thanks for the links. I have already went through them. As these articles point out most of the good performance options are already enabled by default. I tried explicitly enabling socket option TCP_NODELAY and it didn't make a difference.

---

### Post by raghu1111 on 2009-06-25
I was surprised by lack of insight even on Samba mailing lists. Looks like the problem is that SMB clients send one SMB packet for each application write(). So if the app writes smaller writes, it gets very low throughput. I know SMB protocol does not have pipelining but wish client buffered smaller application writes.

To illustrate this, try this on the client :
 'dd if=/dev/zero of=/samba/share/x bs=1k' will get you around 1MB/s
but
 'dd if=/dev/zero of=/samba/share/x bs=64k' will get 8-9MB/s, saturating 100Mbps like

btw, the thread I asked about this on samaba mailing lists : [http://www.nabble.com/Very-slow-transfers-to-Samba-on-Ubuntu-td24168452.html](http://www.nabble.com/Very-slow-transfers-to-Samba-on-Ubuntu-td24168452.html)

<rant>
Please don't get me wrong but, just referring users to long and outdated documents without any useful comment is not at all useful.. especially even after providing a lot of details on the problem. I am pretty sure most "experts" that urge setting SNDBUF to 8192, don't know what it actually means.</rant>

---

### Post by blueridgedog on 2009-06-25
As you are obviously comfortable with Linux, have you considered testing larger values for Read Size and Max Xmit given you have traced it to disk writes?  It would be easy to test given you setup.

---

### Post by seachnasaigh on 2009-06-27
Raghu:

This looks like an interesting problem, but I'd really like a lot more information before offering any advice (or simply saying wtf?).

You said you're on a 100Mbps connexion, with a router. Your tcpdump shows that both machines are on the same subnet, so technically speaking, you're not routing there; the same connexion could be achieved with something as rudimentary as a hub. Can you offer some detail about your network setup? Do you have more than one collision domain (so that you would, in fact, have to route) or are these machines on a home-type network? What kind of gear is the network's heart (I mean, are we dealing with something sophisticated like a Cisco 3750 GW layer-3 switch or something like a COTS linksys home wireless router), and how are the machines connected (i.e., glass, wireless, copper, etc)?

I'm not 100% sure I understand your base configuration (the Irish are dense sometimes). You said that you "mounted an SMB volume on XP". Strictly speaking, XP folks don't mount volumes ... they map drives or map shares. I'm not sure what you've done here but details would be helpful. Also: is this XP home, or pro? And is this an AD, or a Workgroup (from XP's standpoint)? and, is the Ubuntu server (oops, wait ... is it a server or a desktop client machine?) a member of the same workgroup? if AD, is it a member of the AD or a foreign share? Is the Win machine running its baby firewall? On your smb config, have you got winbindd running? and what security perms are on the ubuntu side? do you have a packet-filter running? iptables? apparmour?

The reason I ask all these things is that I think, before analysing the problem from an smb standpoint, we need to ensure that this is an smb problem. So many things can get in the way, and Windows handles file transfers differently on tcp80 than it does on tcp137, or udp139 for example. I have a large file repository running SMB with many shares, and I do not see the kind of performance issues you do ... but my setup could be so different as to render the comparison meaningless. Love to dig into this more.

cheers!

---

### Post by raghu1111 on 2009-06-27
This is a home network. "router" here is is swith+router. Both machines are on the same subnet through a switch.

Yes, I "mapped the network drive drive" on my XP Home (SP3). I used "mounted" by habit. 

I clearly mentioned that I didn't change any thing Samba server config other than adding shares. I think that should answer many of your configuration question. 

Look, obviously Samba and SMB complicated.. but I was looking for educated guess about common cause in common set up. Expecting me to learn about every minute detail and list it here before some one even takes a guess as to what could be the problem is extremely impractical. For.e.g out of so many questions you asked do you know which of those (if any) affect the bandwidth of the transfer? Alternately do you know which ones don't affect transfer rate and not ask those? 

thanks for looking into the problem.

---

### Post by raghu1111 on 2009-06-27
Btw, I already described the reason for slow transfer. Search for 'dd' in the thread. It is inherent problem in SMB protocol. Also please read my earlier comments as well.. I narrowed the it to SMB quite clearly before finding the root cause.

---

### Post by seachnasaigh on 2009-06-28
Raghu:

Actually, it's quite reasonable to understand all of the details of what you're doing to isolate the cause. That's what people like me do every day for a living. And yes, I'm quite aware of which questions I asked might affect transfer speed, and which might cancel the transfer altogether. However, I'd still like to get back to your original problem.

One question I did not ask yet: did you initiate the file transfer from the Windows machine, or from the Ubuntu one? And have you tried it the other way with identical results?

I use smb every day at work; we have a network file share resource which includes 50+ shares, all of them hosted on an smb server in a Windows AD domain. The clients see the shares as just another network drive. We've experienced no latency or slow file transfer such as you describe; in fact, the clients never noticed when we switched the Win2K3 NAS for a smb server on Linux. If anything, we saw some performance increase. What I'm trying to determine is what in my environment is different from yours that might make that latency appear, in the hopes that, should it ever appear, we can get to the root problem quickly.

Cheers.

---


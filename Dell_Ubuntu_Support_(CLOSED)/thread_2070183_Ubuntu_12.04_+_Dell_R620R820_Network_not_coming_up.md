---
title: "Ubuntu 12.04 + Dell R620/R820: Network not coming up"
date: 2012-10-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dheerajkabra on 2012-10-12
Hi all,

I have 3 servers with me: Dell R810, R820 and R620

If I boot up above 3 servers with CentOS 6.3 64-bit Live CD, all of them pickup the IP address and are on the network

But When I boot up these 3 servers with Ubuntu 12.04 64-bit (I have to actually go through the installation as there is no LIVECD version of ubuntu server), then only R810 picks up the Ip address while other do not, even through ubuntu is able to detect all the 4 Ethernet adapters on R620 as well as on R820.

I tried restarting the networking and dhclient stuff, but it is not able to pick up the IP address. 

Is there anything I am missing OR has anyone else faced this issue??

-Thanks.

---

### Post by dheerajkabra on 2012-10-13
I just found on the DEll site for the R620 technical details @ [http://i.dell.com/sites/content/shared-content/data-sheets/en/Documents/dell-poweredge-r620-technical-guide.pdf]("http://i.dell.com/sites/content/shared-content/data-sheets/en/Documents/dell-poweredge-r620-technical-guide.pdf")

On page 11, for suported OS, it mentioned RHEL and SLES but there is no mention of ubuntu/debian...etc.

So I guess it is hopeless to make ubuntu work on R620.

---


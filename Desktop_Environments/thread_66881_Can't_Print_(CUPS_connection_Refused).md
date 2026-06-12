---
title: "Can't Print (CUPS connection Refused)"
date: 2005-09-18
forum: Desktop Environments
---

### Post by _axiom_ on 2005-09-18
My main problem is that can't print anything.  This was all working not too long ago.  When I try to configure printing with kcontrol it says that the connetion to CUPS was refused.

Indeed when I try to configure CUPS with 127.0.0.1:631 I get connection refuesed.  I get the same thing when I try to access webmin on port 10000.

I had an apache server running for testing php code, and now that also says connection refused.  In addtion I cannot ssh to 127.0.0.1, which I could do before.

I discern that these things are somehow related, although I would be happy at the momet if I could just print agian.  Is the some sort of reverse firewall going on here that is blocking all these things from me?

---

### Post by Takis on 2005-09-18
Could you please type 'ifconfig' at a shell?

---

### Post by _axiom_ on 2005-09-18
axiom@axiom:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:8D:A4:32:83
          inet addr:216.229.237.115  Bcast:216.229.239.255  Mask:255.255.248.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:936794 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30911 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:115328744 (109.9 MiB)  TX bytes:4765189 (4.5 MiB)
          Interrupt:19 Base address:0xac00

axiom@axiom:~$

---

### Post by _axiom_ on 2005-09-18
For some reason I took to loopback out of my interfaces file.

Normal people shouldn't edit that file.  

Thanks for pointing me there, I've got it working now.

---


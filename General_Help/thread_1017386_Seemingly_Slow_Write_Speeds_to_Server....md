---
title: "Seemingly Slow Write Speeds to Server..."
date: 2008-12-21
forum: General Help
---

### Post by falconed7 on 2008-12-21
Hey everyone!

I have just built a home server running on Ubuntu Server 8.04.1 and everything is running great except for write speeds to the server over Ethernet (through a router) from a Vista PC.

I am getting constant speeds around 5MB/s to 12MB/s and to me this seems very slow. It took almost an hour to copy 14GB over to the server.

I am wondering if this is normal, or is something definitely wrong?

If it helps my router is a Netgear DG834G

Cheers.

---

### Post by jpkotta on 2008-12-22
If you have 100Mbit ethernet (likely), then 12.5MByte is the absolute theoretical maximum thoughput.  If all of your hardware is 1000Mb, it should automatically use the highest speed, and the throughput will probably be bounded by the hard drives instead.

---


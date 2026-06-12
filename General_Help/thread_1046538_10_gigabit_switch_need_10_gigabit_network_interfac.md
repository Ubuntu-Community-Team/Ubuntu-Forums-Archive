---
title: "10 gigabit switch need 10 gigabit network interface card?"
date: 2009-01-21
forum: General Help
---

### Post by bigmaple on 2009-01-21
Hi,

I want to build a cluster. Since 10 gigabit swith is very fancy, but I can not afford 10 gigabit network interface card which is about $500 each. My concern is that if I have 10 gigabit switch, the 10 gigabit NIC is necessary? I just want to know if the onboard 1 gigabit NIC card can do the job with 10 gigabit switch.

Thanks

---

### Post by Titan8990 on 2009-01-21
Yes, but this defeats the purpose of the 10Gbit switch. Just get a standard 1Gbit switch.

---

### Post by jerome1232 on 2009-01-21
You won't get 10 gb speeds with a 1 gb nic, you will get 1 gb speeds.

For example my home network has a 10/100 mbps switch, connecting 4 computers to a 10/100 mbps router.

One computer is very old, it has a 10 mbps nic, it connects at 10 mbps while the rest of the network connects at the 100 mbps that the switch allows.

---

### Post by DeMus on 2009-01-21
> **bigmaple said:**
> Hi,

I want to build a cluster. Since 10 gigabit swith is very fancy, but I can not afford 10 gigabit network interface card which is about $500 each. My concern is that if I have 10 gigabit switch, the 10 gigabit NIC is necessary? I just want to know if the onboard 1 gigabit NIC card can do the job with 10 gigabit switch.

Thanks

Only supercomputers will work on full speed with a 10Gbit network. Getting a 1 Gbit network to full speed is hard already.

---


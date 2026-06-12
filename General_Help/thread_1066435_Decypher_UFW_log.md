---
title: "Decypher UFW log"
date: 2009-02-10
forum: General Help
---

### Post by AliTabuger7 on 2009-02-10
```
[UFW ALLOW INPUT]: IN=eth0 OUT= MAC=00:04:4b:06:7d:e8:00:02:XX:XX:XX:XX:XX:XX SRC=68.146.254.XXX DST=131.156.249.XXX LEN=60 TOS=0x00 PREC=0x00 TTL=49 ID=18488 DF PROTO=TCP SPT=54726 DPT=51298 WINDOW=5840 RES=0x00 SYN URGP=0 
```

Can someone tell me which one is the port number?

---

### Post by mobilediesel on 2009-02-11
> **AliTabuger7 said:**
> ```
[UFW ALLOW INPUT]: IN=eth0 OUT= MAC=00:04:4b:06:7d:e8:00:02:XX:XX:XX:XX:XX:XX SRC=68.146.254.XXX DST=131.156.249.XXX LEN=60 TOS=0x00 PREC=0x00 TTL=49 ID=18488 DF PROTO=TCP SPT=54726 **[COLOR="Red"]DPT=51298[/COLOR]** WINDOW=5840 RES=0x00 SYN URGP=0 
```

Can someone tell me which one is the port number?

**[COLOR="Red"]DPT=51298[/COLOR]** is the port.

---


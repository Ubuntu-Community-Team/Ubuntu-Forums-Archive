---
title: "Intermittent remote printintg"
date: 2006-06-11
forum: Desktop Environments
---

### Post by lduperval on 2006-06-11
HI,

I updated to Dapper this week and I ahave been experiencing some printing issues.

I have an HP Laserjet 3015 which workd fine. Problem is that when I print remotely from my laptop, it doesn't always work. If I print from the Dapper machine (my desktop) I always get correct output. However, when I print from my laptop, sometimes it prints, sometimes it doesn't.

For example, I will print a document in OpenOffice from my laptop and it works fine. Then I will print another document from OO on my laptop and it won't print. When I look at the CUPS web interface for my laptop, it says it is trying to connect to 

Connecting to mydesktop on port 631

but does nothing. The jobs are queued, the status says Idle and accepting print jobs.

Does anyone know what could be going on?

L

---

### Post by lduperval on 2006-06-11
I just noticed that in the messages file, I get a lot of these:

```

Jun 11 00:10:17 localhost kernel: [4306059.992000] Inbound IN=eth0 OUT= MAC=XXXX SRC=192.168.1.101 DST=192.168.1.2 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=26375 DF PROTO=TCP SPT=54966 DPT=631 WINDOW=5840 RES=0x00 SYN URGP=0

```

I don't know if it means anything in particular.

L

---

### Post by lduperval on 2006-06-11
Well, it looks like the firewal was blocking the printing. Some how, the IP address of my laptop changed, and that caused the problem. 

L

---


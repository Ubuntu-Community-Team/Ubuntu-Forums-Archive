---
title: "log file I don't understand...please explain"
date: 2005-08-03
forum: Desktop Environments
---

### Post by kittcankitt on 2005-08-03
I was going through some of the log files in /var/log this morning and noticed that four of the log files were almost identical.  The files in question are: syslog, kern.log, daemon.log, and messages.  Now I do actually have a question (2 really) because they are all reporting the same thing:

"Aug  3 09:30:02 localhost kernel: Inbound IN=ppp0 OUT= MAC= SRC=67.68.188.155 DST=67.68.188.6 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=60344 DF PROTO=TCP SPT=3344 DPT=445 WINDOW=64800 RES=0x00 SYN URGP=0
Aug  3 09:30:05 localhost kernel: Inbound IN=ppp0 OUT= MAC= SRC=67.68.188.155 DST=67.68.188.6 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=61263 DF PROTO=TCP SPT=3344 DPT=445 WINDOW=64800 RES=0x00 SYN URGP=0
Aug  3 09:30:21 localhost kernel: Inbound IN=ppp0 OUT= MAC= SRC=218.66.104.151 DST=67.68.188.6 LEN=382 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=UDP SPT=32774 DPT=1029 LEN=362
Aug  3 09:30:21 localhost kernel: Inbound IN=ppp0 OUT= MAC= SRC=218.66.104.151 DST=67.68.188.6 LEN=382 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=UDP SPT=32774 DPT=1027 LEN=362
Aug  3 09:30:21 localhost kernel: Inbound IN=ppp0 OUT= MAC= SRC=218.66.104.151 DST=67.68.188.6 LEN=382 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=UDP SPT=32774 DPT=1026 LEN=362
Aug  3 09:30:21 localhost kernel: Inbound IN=ppp0 OUT= MAC= SRC=218.66.104.151 DST=67.68.188.6 LEN=382 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=UDP SPT=32774 DPT=1028 LEN=362
Aug  3 09:30:29 localhost kernel: Inbound IN=ppp0 OUT= MAC= SRC=222.141.93.27 DST=67.68.188.6 LEN=466 TOS=0x00 PREC=0x00 TTL=42 ID=0 DF PROTO=UDP SPT=39810 DPT=1026 LEN=446
Aug  3 09:30:29 localhost kernel: Inbound IN=ppp0 OUT= MAC= SRC=222.141.93.27 DST=67.68.188.6 LEN=466 TOS=0x00 PREC=0x00 TTL=42 ID=0 DF PROTO=UDP SPT=39810 DPT=1027 LEN=446
Aug  3 09:30:36 localhost kernel: Inbound IN=ppp0 OUT= MAC= SRC=67.68.190.69 DST=67.68.188.6 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=6636 DF PROTO=TCP SPT=4717 DPT=445 WINDOW=64800 RES=0x00 SYN URGP=0
Aug  3 09:30:39 localhost kernel: Inbound IN=ppp0 OUT= MAC= SRC=67.68.190.69 DST=67.68.188.6 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=7730 DF PROTO=TCP SPT=4717 DPT=445 WINDOW=64800 RES=0x00 SYN URGP=0"

and it goes on.  As you can see it is logging this every 3-6 seconds!? in all four files.  My questions are can I safely delete the corresponding ...2.gz ....3.gz files assuming they are of no longer importance? and secondly, what isn't configured right to be giving me log files like this.  If/when I ever have to tail -f /var/log/messages, I have to filter through all the rest of the garbage first.

I am a single pc connected to a dsl modem on eth0 and all is working well.  Any ideas?

---

### Post by grim42 on 2005-08-03
This looks to me like incoming network traffic being logged. I'm not sure if this means it's being blocked by the kernel's IP filtering (firewall).

Do you have something like Firestarter installed and configured to log network traffic?

---

### Post by sbassett on 2005-08-03
[QUOTE=grim42]This looks to me like incoming network traffic being logged. I'm not sure if this means it's being blocked by the kernel's IP filtering (firewall).

Do you have something like Firestarter installed and configured to log network traffic?[/QUOTE]
 Definetly get a firewall up. And if you are on cable, get a router. These are sweeping for MS SMB ports(445) and the infamous 102x ports.

---

### Post by nocturn on 2005-08-04
About the replication of log entries.
All log messages go through the syslog program which desides what to do with them.
Syslog is controlled by a file in /etc (I think syslog.conf).

Each message also has a facility to indicate the kind of message (like info).  You can set up syslog to only log some types of messages, or to categorize them in several places.  The default setup however writes everything to /var/log/messages or /var/log/syslog, replicating the entries.

---

### Post by kittcankitt on 2005-08-04
Yes, I do have firestarter and snort installed.   Firestarter logs almost exclusively those common ports as stated above.  Thanks for the responses/explanations I will have a look at he configuration file and see if I can try to get the messages narrowed down to at least one log file.  Look out google, here I come!  

Thanks again!  KCK

---


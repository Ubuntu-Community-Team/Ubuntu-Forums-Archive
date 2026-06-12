---
title: "Computer halts when online (hack attempt?)"
date: 2006-02-26
forum: Desktop Environments
---

### Post by alfotis on 2006-02-26
Hi all, 

I have an extremely annoying problem. Sometimes, when i'm online, my computer halts. It shuts down normally like someone executed poweroff. Is this a hacker's work or some software problem? This happened ONLY when i was online. 

I use firestarter as a firewall, wvdial to dial out, firefox to browse. 


Here's what /var/log/messages said:

```

3 DF PROTO=TCP SPT=80 DPT=34848 WINDOW=6432 RES=0x00 ACK URGP=0
Feb 26 18:16:33 localhost kernel: [4424714.203000] Inbound IN=ppp0 OUT= MAC= SRC=195.215.8.138 DST=MY.IP LEN=1500 TOS=0x00 PREC=0x00 TTL=45 ID=52284 DF PROTO=TCP SPT=80 DPT=34848 WINDOW=6432 RES=0x00 ACK URGP=0
Feb 26 18:17:53 localhost kernel: [4424793.502000] Inbound IN=ppp0 OUT= MAC= SRC=195.215.8.138 DST=MY.IP LEN=1500 TOS=0x00 PREC=0x00 TTL=45 ID=52285 DF PROTO=TCP SPT=80 DPT=34848 WINDOW=6432 RES=0x00 ACK URGP=0
Feb 26 18:21:10 localhost shutdown[12717]: shutting down for system halt
Feb 26 18:21:27 localhost gconfd (fotis-8152): Received signal 15, shutting down cleanly
Feb 26 18:21:29 localhost gconfd (fotis-8152): Exiting
Feb 26 18:21:39 localhost shutdown[12843]: shutting down for system halt
Feb 26 18:21:44 localhost kernel: [4425024.562000] apm: BIOS not found.
Feb 26 18:21:56 localhost shutdown[13310]: shutting down for system halt
Feb 26 18:21:58 localhost kernel: Kernel logging (proc) stopped.
Feb 26 18:21:58 localhost kernel: Kernel log daemon terminating.
Feb 26 18:21:58 localhost exiting on signal 15
Feb 26 18:24:03 localhost syslogd 1.4.1#17ubuntu3: restart.
Feb 26 18:24:03 localhost kernel: Inspecting /boot/System.map-2.6.12-10-386
Feb 26 18:24:04 localhost kernel: Loaded 29010 symbols from /boot/System.map-2.6.12-10-386.
Feb 26 18:24:04 localhost kernel: Symbols match kernel version 2.6.12.
Feb 26 18:24:04 localhost kernel: No module symbols loaded - kernel modules not enabled.
Feb 26 18:24:04 localhost kernel: 1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)

``` and then continues with boot...

Can anyone please help?

And what are these net entries?

---


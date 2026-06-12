---
title: "System Freeze, Any ideas?"
date: 2008-12-11
forum: General Help
---

### Post by thumper_e on 2008-12-11
I'm really sorry that I'm going to be very vague, however I have no Idea what the problem stems from.
 Firstly I'm using Intrepid (8.10) The computer freezes and I have to physically switch it off via the power button to get any form of response out of it again. I have checked the logs and have found nothing (That I can see anyway) that might be causing the issue. 

>From the kernel log at time of crash;
Dec 11 18:03:21 study kernel: [12665.937187] Inbound IN=eth1 OUT= MAC= SRC=81.106.137.72 DST=81.106.139.255 LEN=234 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=214 
Dec 11 18:06:19 study kernel: [12844.214684] Inbound IN=eth1 OUT= MAC=00:0c:76:ac:d5:21:00:0a:42:6b:28:01:08:00 SRC=125.65.165.139 DST=81.106.137.72 LEN=40 TOS=0x00 PREC=0x00 TTL=113 ID=256 DF PROTO=TCP SPT=12200 DPT=8000 WINDOW=8192 RES=0x00 SYN URGP=0 

>From the syslog at time of crash;
Dec 11 18:06:19 study kernel: [12844.214684] Inbound IN=eth1 OUT= MAC=00:0c:76:ac:d5:21:00:0a:42:6b:28:01:08:00 SRC=125.65.165.139 DST=81.106.137.72 LEN=40 TOS=0x00 PREC=0x00 TTL=113 ID=256 DF PROTO=TCP SPT=12200 DPT=8000 WINDOW=8192 RES=0x00 SYN URGP=0 
Dec 11 18:06:21 study pulseaudio[6150]: sap.c: sendmsg() failed: Operation not permitted
Dec 11 18:06:56 study last message repeated 7 times
Dec 11 18:08:01 study last message repeated 13 times
Dec 11 18:08:41 study last message repeated 8 times
Dec 11 18:08:44 study dhcpd: DHCPREQUEST for 192.168.0.2 from 00:0c:6e:b1:56:9d (abbie-desktop) via eth0
Dec 11 18:08:44 study dhcpd: DHCPACK on 192.168.0.2 to 00:0c:6e:b1:56:9d (abbie-desktop) via eth0
Dec 11 18:08:46 study pulseaudio[6150]: sap.c: sendmsg() failed: Operation not permitted
Dec 11 18:09:21 study last message repeated 7 times

>From the daemon.log around time of crash;
Dec 11 18:05:33 study hotwayd[14205]: connect from ::ffff:127.0.0.1 (::ffff:127.0.0.1)

>From the user.log at time of crash.
Dec 11 17:06:23 study pulseaudio[6150]: sap.c: sendmsg() failed: Operation not permitted
Dec 11 17:06:58 study last message repeated 7 times
Dec 11 17:08:03 study last message repeated 13 times
Dec 11 17:09:03 study last message repeated 12 times
.
.
.
.
Dec 11 18:06:06 study last message repeated 12 times
Dec 11 18:07:06 study last message repeated 12 times
Dec 11 18:08:06 study last message repeated 12 times
Dec 11 18:09:06 study last message repeated 12 times

This crash could happen several times daily, or not for weeks. and I'm
stumped as to where to start! Any help would be greatly appreciated
before I do A fresh install.

ProblemType: Bug
Architecture: i386
DistroRelease: Ubuntu 8.10
ExecutablePath: /usr/bin/gnome-system-log
NonfreeKernelModules: fglrx
Package: gnome-utils 2.24.1-0ubuntu1
ProcEnviron:
 PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
 LANG=en_GB.UTF-8
 SHELL=/bin/bash
SourcePackage: gnome-utils
Uname: Linux 2.6.27-10-generic i686

---


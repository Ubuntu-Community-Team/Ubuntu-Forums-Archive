---
title: "Help quake server on ubuntu.. How to manage it?"
date: 2014-05-06
forum: Gaming &amp; Leisure
---

### Post by wallace2 on 2014-05-06
[COLOR=#000000]Hello there![/COLOR]

[COLOR=#000000]PLEASE!! I need some help. I am new to Linux and I am actually proud to have made this far by myself.. I installed an Ubuntu 12.04 in a remote computer to run quakeone servers (T-Rex of cpu multiplayer) and I managed to put all the servers ON and running on background with nohup and on tmux. [/COLOR]

[COLOR=#000000]It´s quite painfull to find the waterfall of pendencies to install all libraries to get those servers running.. How do you guys cope with that? Every single thing you need have 2000 dependencies and each one of that has another 2000 heehehe TIRING [/COLOR]:smile:[COLOR=#000000] [/COLOR]

[COLOR=#000000]Well.. let´s go to what matters.[/COLOR]

[COLOR=#000000]What do I need to do to bring this servers from background to foreground and split it? So I could have all the 5 servers in different screens to manage when I was here and when I have to logoff I put the servers in background again. [/COLOR]

[COLOR=#000000]I am using PUTTY. [/COLOR]

[COLOR=#000000]This is what I find when I type TMUX LS [/COLOR]

[COLOR=#000000]0: 1 windows (created Sun May 4 17:18:12 2014) [168x42] (attached)[/COLOR]
[COLOR=#000000]1: 1 windows (created Sun May 4 17:20:01 2014) [80x23][/COLOR]
[COLOR=#000000]10: 1 windows (created Mon May 5 10:35:34 2014) [80x23][/COLOR]
[COLOR=#000000]11: 1 windows (created Mon May 5 10:36:46 2014) [80x22] (attached)[/COLOR]
[COLOR=#000000]12: 1 windows (created Mon May 5 10:37:51 2014) [80x23][/COLOR]
[COLOR=#000000]13: 1 windows (created Mon May 5 10:38:02 2014) [80x22] (attached)[/COLOR]
[COLOR=#000000]14: 1 windows (created Mon May 5 10:55:35 2014) [80x23][/COLOR]
[COLOR=#000000]15: 1 windows (created Mon May 5 10:59:06 2014) [80x22] (attached)[/COLOR]
[COLOR=#000000]16: 1 windows (created Mon May 5 10:59:24 2014) [80x21] (attached)[/COLOR]
[COLOR=#000000]17: 2 windows (created Mon May 5 11:01:55 2014) [80x23][/COLOR]
[COLOR=#000000]18: 1 windows (created Mon May 5 11:06:09 2014) [168x43][/COLOR]
[COLOR=#000000]19: 1 windows (created Mon May 5 11:31:57 2014) [168x45][/COLOR]
[COLOR=#000000]2: 1 windows (created Sun May 4 17:21:24 2014) [80x23][/COLOR]
[COLOR=#000000]20: 1 windows (created Mon May 5 14:31:39 2014) [168x43][/COLOR]
[COLOR=#000000]21: 1 windows (created Mon May 5 14:56:02 2014) [168x43][/COLOR]
[COLOR=#000000]22: 1 windows (created Mon May 5 19:10:38 2014) [168x43] (attached)[/COLOR]
[COLOR=#000000]3: 1 windows (created Sun May 4 17:47:21 2014) [80x23][/COLOR]
[COLOR=#000000]4: 1 windows (created Sun May 4 17:50:08 2014) [80x22] (attached)[/COLOR]
[COLOR=#000000]5: 1 windows (created Sun May 4 19:43:20 2014) [80x23][/COLOR]
[COLOR=#000000]6: 1 windows (created Sun May 4 19:45:18 2014) [80x23][/COLOR]
[COLOR=#000000]7: 1 windows (created Sun May 4 21:33:24 2014) [80x23][/COLOR]
[COLOR=#000000]8: 1 windows (created Sun May 4 21:36:51 2014) [80x22] (attached)[/COLOR]
[COLOR=#000000]9: 1 windows (created Sun May 4 21:37:43 2014) [80x23][/COLOR]


[COLOR=#000000]Why do I have so many windows if I just have 5 servers up? How do I access those windows or close them if I dont need them? How can I identify my server, please?[/COLOR]

[COLOR=#000000]This is the result of the command TOP[/COLOR]


[B]3676 root 20 0 18588 7092 260 S 7.9 1.4 123:17.93 pqlinux
[B]2487 root 19 -1 18592 960 236 S 7.3 0.2 127:31.91 pqlinux
[B]3047 root 20 0 18596 7972 388 S 7.3 1.6 125:28.34 pqlinux
[B]3310 root 20 0 18588 5996 276 S 7.3 1.2 125:08.29 pqlinux
[B]5363 root 20 0 18600 7340 220 S 7.3 1.5 113:00.71 pqlinux
21923 root 20 0 85696 2904 1856 S 0.3 0.6 0:00.85 sshd
23989 root 20 0 17476 1448 972 R 0.3 0.3 0:00.08 top
1 root 20 0 24320 1752 960 S 0.0 0.4 0:02.01 init
2 root 20 0 0 0 0 S 0.0 0.0 0:00.00 kthreadd
3 root 20 0 0 0 0 S 0.0 0.0 0:03.21 ksoftirqd/0
5 root 0 -20 0 0 0 S 0.0 0.0 0:00.00 kworker/0:0H
7 root RT 0 0 0 0 S 0.0 0.0 0:00.04 migration/0
8 root 20 0 0 0 0 S 0.0 0.0 0:00.00 rcu_bh
9 root 20 0 0 0 0 S 0.0 0.0 0:00.00 rcuob/0
10 root 20 0 0 0 0 S 0.0 0.0 0:00.00 rcuob/1
11 root 20 0 0 0 0 S 0.0 0.0 0:00.00 rcuob/2
12 root 20 0 0 0 0 S 0.0 0.0 0:00.00 rcuob/3
13 root 20 0 0 0 0 S 0.0 0.0 0:00.00 rcuob/4
14 root 20 0 0 0 0 S 0.0 0.0 0:00.00 rcuob/5
15 root 20 0 0 0 0 S 0.0 0.0 0:00.00 rcuob/6
16 root 20 0 0 0 0 S 0.0 0.0 0:00.00 rcuob/7
17 root 20 0 0 0 0 S 0.0 0.0 0:00.00 rcuob/8
18 root 20 0 0 0 0 S 0.0 0.0 0:00.00 rcuob/9
19 root 20 0 0 0 0 S 0.0 0.0 0:00.00 rcuob/10
20 root 20 0 0 0 0 S 0.0 0.0 0:00.00 rcuob/11
21 root 20 0 0 0 0 S 0.0 0.0 0:00.00 rcuob/12
22 root 20 0 0 0 0 S 0.0 0.0 0:00.00 rcuob/13
23 root 20 0 0 0 0 S 0.0 0.0 0:00.00 rcuob/14
24 root 20 0 0 0 0 S 0.0 0.0 0:00.00 rcuob/15
25 root 20 0 0 0 0 S 0.0 0.0 0:00.00 rcuob/16
26 root 20 0 0 0 0 S 0.0 0.0 0:00.00 rcuob/17
27 root 20 0 0 0 0 S 0.0 0.0 0:00.00 rcuob/18
28 root 20 0 0 0 0 S 0.0 0.0 0:00.00 rcuob/19
29 root 20 0 0 0 0 S 0.0 0.0 0:00.00 rcuob/20
30 root 20 0 0 0 0 S 0.0 0.0 0:00.00 rcuob/21
31 root 20 0 0 0 0 S 0.0 0.0 0:00.00 rcuob/22

The first 5 are my servers, the rest I dont know.

How can I open one of the servers console, please?

Well, that´s it for now.. I have the servers running but I cant manage them :smile: 

Thanks in advance for any reply.

W3[/B][/B][/B][/B][/B]

---

### Post by coffeecat on 2014-05-06
Closed. Please do not post duplicates in different places.

---


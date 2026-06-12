---
title: "bzflag segfaults"
date: 2006-06-11
forum: Gaming &amp; Leisure
---

### Post by probe45 on 2006-06-11
Hey,

I installed a fresh copy of ubuntu 6.06 with nvidia-drivers and my favorite game bzflag (2.0.4?? mhh 2.0.8 is out allready for some time but oke). After the installation I wanted to play a game of bzflag and like allways it did start normal so I did set the game settings how I like them and started to play..

For a full 3 minuts I played and everything whent well untill suddently I was trown back at the desktop :(

Oke not knowing what the problem was I tried looking it up in the logs but nothing there So I retried and again after 3 minuts back at the desktop leaving me totaly blanc.

Because I wanted to know what happend I peformed a strace and I cant do anything with its output now becaue I simply dont understand it (yet)
The output file gave me this (only the tail since its long)

> gettimeofday({1150065993, 727215}, NULL) = 0
gettimeofday({1150065993, 727272}, NULL) = 0
recvfrom(12, 0x898a998, 1024, 0, 0x898a96c, 0xbfed219c) = -1 EAGAIN (Resource temporarily unavailable)
select(11, [10], NULL, NULL, {0, 0})    = 0 (Timeout)
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
gettimeofday({1150065993, 727725}, NULL) = 0
gettimeofday({1150065993, 727810}, NULL) = 0
gettimeofday({1150065993, 727850}, NULL) = 0
gettimeofday({1150065993, 727910}, NULL) = 0
gettimeofday({1150065993, 727953}, NULL) = 0
gettimeofday({1150065993, 727992}, NULL) = 0
gettimeofday({1150065993, 728034}, NULL) = 0
gettimeofday({1150065993, 728073}, NULL) = 0
gettimeofday({1150065993, 728126}, NULL) = 0
gettimeofday({1150065993, 728168}, NULL) = 0
gettimeofday({1150065993, 733769}, NULL) = 0
gettimeofday({1150065993, 733825}, NULL) = 0
gettimeofday({1150065993, 733863}, NULL) = 0
time([1150065993])                      = 1150065993
gettimeofday({1150065993, 737813}, NULL) = 0
gettimeofday({1150065993, 737869}, NULL) = 0
recvfrom(12, "\0\33psC\321i*\f\0\0\2p\0A\27\327!4\3\255\377\274\374\251"..., 1024, 0, {sa_family=AF_INET, sin_port=htons(5158), sin_addr=inet_addr("217.20.127.212")}, [16]) = 31
recvfrom(12, 0x898a998, 1024, 0, 0x898a96c, 0xbfed219c) = -1 EAGAIN (Resource temporarily unavailable)
select(11, [10], NULL, NULL, {0, 0})    = 0 (Timeout)
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
gettimeofday({1150065993, 738633}, NULL) = 0
gettimeofday({1150065993, 738717}, NULL) = 0
gettimeofday({1150065993, 738760}, NULL) = 0
gettimeofday({1150065993, 738844}, NULL) = 0
gettimeofday({1150065993, 739234}, NULL) = 0
gettimeofday({1150065993, 739351}, NULL) = 0
gettimeofday({1150065993, 739397}, NULL) = 0
gettimeofday({1150065993, 739441}, NULL) = 0
gettimeofday({1150065993, 739480}, NULL) = 0
gettimeofday({1150065993, 739519}, NULL) = 0
gettimeofday({1150065993, 739557}, NULL) = 0
gettimeofday({1150065993, 739619}, NULL) = 0
gettimeofday({1150065993, 739661}, NULL) = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
rt_sigaction(SIGSEGV, {SIG_DFL}, {0x8122ae0, [], 0}, 8) = 0
tgkill(6047, 6047, SIGSEGV)             = 0
sigreturn()                             = ? (mask now [])
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++
pardoes@ubuntu:~$



Does someone know what I must do to repair this problem?

thx in adv :)

---

### Post by Straker on 2006-07-19
I have breezy and BZFLAG just quit working for me too.  My problem seems to be an SDL issue, but just stopped working after a recent update process and reboot.  I think a recent SDL package update may be to blame.

seeking expert replies....

---


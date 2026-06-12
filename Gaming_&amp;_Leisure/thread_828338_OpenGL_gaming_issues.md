---
title: "OpenGL gaming issues"
date: 2008-06-13
forum: Gaming &amp; Leisure
---

### Post by v4169sgr on 2008-06-13
Dear all,

I realise I may not have achieved replies to this previous thread because (a) it may have been posted in the wrong forum, and (b) it was not specific enough:

[http://ubuntuforums.org/showthread.php?t=825106]("http://ubuntuforums.org/showthread.php?t=825106")

I've also learned a little more about my issues. So, I'll start again.

System properties attached. Nvidia properties attached. Installed driver screenie attached.

[ATTACH]73958[/ATTACH]

[ATTACH]73959[/ATTACH]

[ATTACH]73963[/ATTACH]

Issues:

1. Frozen bubble wont play past the menus.[ATTACH]73966[/ATTACH] On display of this menu, the game freezes and has to be killed from the shell.

2. Neverball plays real nice, very smooth and with no problems, but will not exit. Again has to be killed.

What I have learned:

a. CPU cycles are a red herring. Accelerated graphics games are meant to take lots of CPU cycles. That's the nature of the beast. glxgears runs fine and takes lots of CPU too. And it doesn't need to be killed :)

b. The issues have nothing to do with compiz. I ran compiz -- replace on the foreground from the shell [after taking precautions], and Cntl-C'ed it. Window decorations, switcher all went, so compiz obviously dead on the floor, and the games still had the issues as described.

What am I doing wrong?:confused:

---

### Post by v4169sgr on 2008-06-13
strace frozen-bubble at the affected stage shows this over and over:

```
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
gettimeofday({1213393995, 410704}, NULL) = 0
nanosleep({0, 19000000}, {0, 19000000}) = 0
gettimeofday({1213393995, 429889}, NULL) = 0
read(3, 0x8a18b84, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
read(3, 0x8a18b84, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
gettimeofday({1213393995, 430284}, NULL) = 0
nanosleep({0, 20000000}, {0, 20000000}) = 0
gettimeofday({1213393995, 450486}, NULL) = 0
read(3, 0x8a18b84, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
read(3, 0x8a18b84, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
gettimeofday({1213393995, 450699}, NULL) = 0
nanosleep({0, 19000000}, {0, 19000000}) = 0
gettimeofday({1213393995, 470902}, NULL) = 0
read(3, 0x8a18b84, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
read(3, 0x8a18b84, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
gettimeofday({1213393995, 471121}, NULL) = 0
nanosleep({0, 20000000}, {0, 20000000}) = 0
gettimeofday({1213393995, 491303}, NULL) = 0
read(3, 0x8a18b84, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
read(3, 0x8a18b84, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
gettimeofday({1213393995, 491717}, NULL) = 0
nanosleep({0, 19000000}, {0, 19000000}) = 0
gettimeofday({1213393995, 510965}, NULL) = 0
read(3, 0x8a18b84, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
read(3, 0x8a18b84, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
gettimeofday({1213393995, 511170}, NULL) = 0
nanosleep({0, 20000000}, {0, 20000000}) = 0
gettimeofday({1213393995, 532383}, NULL) = 0
read(3, 0x8a18b84, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
read(3, 0x8a18b84, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
gettimeofday({1213393995, 532603}, NULL) = 0

```

---

### Post by v4169sgr on 2008-06-14
I am not sure I even fully understand the issues. Here again are some observations:

* These games did NOT take 100% CPU on Dapper, but they do on Hardy.

* Freeciv client seems to require a forcekill to close the window, and again takes 100% CPU - per window - which it never did in Dapper. Also, one user doesn't have sound, while the other does.

What is going on?

---

### Post by v4169sgr on 2008-06-14
Observation: Only the freeciv client with sound issues required a forcekill.

---

### Post by v4169sgr on 2008-06-14
There is a connection:

All those applications with issues [freeciv, maelstrom, neverball] **have no sound ...**

/me stares down the nozzle of a smoking gun barrel

---

### Post by v4169sgr on 2008-06-16
Solved, here:

[http://ubuntuforums.org/showthread.php?p=5199607#post5199607](http://ubuntuforums.org/showthread.php?p=5199607#post5199607)

---


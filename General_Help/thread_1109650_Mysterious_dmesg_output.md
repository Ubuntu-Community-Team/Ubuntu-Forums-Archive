---
title: "Mysterious dmesg output"
date: 2009-03-29
forum: General Help
---

### Post by gmatt on 2009-03-29
Hi,

I am receiving some mysterious dmesg output and I was wondering if someone could help point me in the right direction.

```

[21815.828481] __ratelimit: 6 callbacks suppressed
[21815.828492] compiz.real[15719]: segfault at 150 ip 08055c8c sp bfd801e0 error 4 in compiz.real[8048000+34000]
[21840.896353] canberra-gtk-pl[16391]: segfault at 4cc81088 ip b71fd84d sp b6f9af10 error 6 in libpulse.so.0.4.1[b71be000+4e000]
[21874.482525] Too big adjustment 32
[21874.522738] Too big adjustment 32
[21929.571704] Too big adjustment 32
[21929.610740] Too big adjustment 32
[21955.079908] Too big adjustment 32
[21955.119099] Too big adjustment 32
[22021.753366] Too big adjustment 32
[22021.794155] Too big adjustment 32


```


then before that it was 

```
 
[21372.325316] Too big adjustment 32
[21372.370196] Too big adjustment 32
[21395.491619] Too big adjustment 32
[21395.530885] Too big adjustment 32
[21407.918829] NVRM: Xid (0001:00): 13, 0004 00000000 00008397 00001458 00000006 00000100
[21408.134088] NVRM: Xid (0001:00): 13, 0004 00000000 00008397 00001458 00000006 00000100
[21409.288633] NVRM: Xid (0001:00): 13, 0004 00000000 00008397 00001458 00000006 00000100
[21410.488434] NVRM: Xid (0001:00): 13, 0004 00000000 00008397 00001458 00000006 00000100
[21410.751504] NVRM: Xid (0001:00): 13, 0004 00000000 00008397 00001458 00000006 00000100
[21563.680100] __ratelimit: 6 callbacks suppressed
[21563.680108] compiz.real[6419]: segfault at 35373839 ip 08055c8c sp bf998510 error 4 in compiz.real[8048000+34000]
[21613.694649] Too big adjustment 32
[21613.734399] Too big adjustment 32
[21631.757881] NVRM: Xid (0001:00): 13, 0004 00000000 00008397 00001458 00000006 00000100
[21631.976429] NVRM: Xid (0001:00): 13, 0004 00000000 00008397 00001458 00000006 00000100


```

What could cause this? Specifically, what does the line Too big adjustment 32 mean, what is spitting that out?

---

### Post by hikaricore on 2009-04-23
I'd kinda like to know the secret of:

> Too big adjustment 32

As well if anyone has any ideas.  :p

---

### Post by Yashiro on 2009-04-23
Looks like a reference to a video issue. Texture block size maybe.
Update your nvidia driver.

---

### Post by hikaricore on 2009-04-23
> [  202.864839] Too big adjustment 32
[  202.904015] Too big adjustment 32
[  202.945479] Too big adjustment 32
[  202.952018] Too big adjustment 32
[  202.969373] Too big adjustment 32
[  202.977509] Too big adjustment 32
[  202.986949] Too big adjustment 32
[  202.993508] Too big adjustment 32
[  203.009252] Too big adjustment 32
[  203.040007] Too big adjustment 32
[  203.073421] Too big adjustment 32
[  203.080008] Too big adjustment 32
[  203.097076] Too big adjustment 32
[  203.128016] Too big adjustment 32
[  203.161446] Too big adjustment 32
[  203.168017] Too big adjustment 32
[  203.185021] Too big adjustment 32
[  203.216016] Too big adjustment 32
[  203.249450] Too big adjustment 32
[  203.256008] Too big adjustment 32
[  203.272932] Too big adjustment 32
[  203.304015] Too big adjustment 32
[  203.337434] Too big adjustment 32
[  203.344016] Too big adjustment 32
[  203.360926] Too big adjustment 32
[  203.392016] Too big adjustment 32
[  203.425422] Too big adjustment 32
[  203.432017] Too big adjustment 32
[  203.449874] Too big adjustment 32
[  203.457508] Too big adjustment 32


I'm seeing nothing in relation to video errors, I believe that part of the OP's dmesg output is circumstantial..

---

### Post by manuelb on 2009-04-23
It seems an [audio related]("https://bugzilla.redhat.com/show_bug.cgi?id=489154") issue, ALSA + Intel HDA.

---

### Post by HDave on 2009-09-28
Anyone get to the bottom of this?  I am getting this too...

---

### Post by argos277 on 2009-10-20
I have a Pc with Pentium D processor, 2GB DDR, Ubuntu 9.04 and a Nvidia 8400gs video card. Suddenly, meanwhile I used XBMC or a Wine game, the system hangs up. My monitor (Dell 2209w) blinks, the mouse and the keyboard not responding. I read the syslog and I found Too big adjustment 32 message. Someone knows why occur that?

---


---
title: "hald problem when cd is in device"
date: 2007-05-24
forum: Desktop Environments
---

### Post by ubeczek on 2007-05-24
Ok problem appears to be unknown in this site so:

 PID USER PR NI VIRT RES SHR S %CPU %MEM TIME+ COMMAND
4969 haldaemo 25 0 3044 1228 1076 R 99.8 0.3 0:45.48 hald-addon-stor
5758 ubek 15 0 2316 1164 880 R 0.4 0.3 0:01.06 top
1 root 15 0 2912 1844 524 S 0.0 0.5 0:01.22 init
2 root RT 0 0 0 0 S 0.0 0.0 0:00.00 migration/0
3 root 34 19 0 0 0 R 0.0 0.0 0:00.00 ksoftirqd/0
4 root RT 0 0 0 0 S 0.0 0.0 0:00.00 watchdog/0
5 root 10 -5 0 0 0 S 0.0 0.0 0:00.05 events/0
6 root 10 -5 0 0 0 S 0.0 0.0 0:00.00 khelper
7 root 10 -5 0 0 0 S 0.0 0.0 0:00.00 kthread
30 root 10 -5 0 0 0 S 0.0 0.0 0:00.00 kblockd/0

as you can see hald deamon is tacking all of cpu usage. This problem appears when I insert cd to device.
step by step its like:
1. I insert cd rom
2. hald open cd rom
3. by 30-40 min I can use cd with no problem
4. after that system is completely dysfunctional

in this case only what I can do is
ubek@ubek-laptop:~$ sudo kill -9 4969

place give me an advice

---


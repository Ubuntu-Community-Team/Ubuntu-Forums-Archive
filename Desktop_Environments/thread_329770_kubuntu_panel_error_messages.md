---
title: "kubuntu panel error messages"
date: 2007-01-02
forum: Desktop Environments
---

### Post by fredds on 2007-01-02
Hi all; I am getting error messages whenever I start any program, saying  "a program called foo is slowing down the others on your machine".  Fortunately it gives the option to ignore it and future messages about that program.  The programs work correctly and system guard does not show the processor overworking.
I have Googled for an answer, but nothing applies to this problem.
Searched the forums here, nothing again; could be my search skills are not good.
Have been using Ubuntu hoary, warty, dapper previously with no problems.
Running 32bit edgy on AMD64X2 3800

Thanks
Fredd

---

### Post by bernied on 2007-01-02
Have a look at running processes, using top (in a terminal). Here's what mine (right now) looks like:
```
~$ top
13:17:08 up 20:25,  1 user,  load average: 0.47, 0.63, 0.82
Tasks: 107 total,   1 running, 106 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.6%us,  0.3%sy,  0.0%ni, 95.7%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:    775584k total,   743672k used,    31912k free,     3092k buffers
Swap:  1124536k total,    20012k used,  1104524k free,   509628k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4802 bernie    15   0  135m  43m  26m S  3.0  5.7  11:00.41 amarokapp
 4220 root      15   0  419m  67m 5728 S  0.3  8.9  12:13.82 Xorg
    1 root      16   0  1628  532  448 S  0.0  0.1   0:01.03 init
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0
    3 root      34  19     0    0    0 S  0.0  0.0   0:01.71 ksoftirqd/0
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.04 events/0
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 khelper
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.59 kblockd/0
   10 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   11 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify
   85 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kseriod
  118 root      15   0     0    0    0 S  0.0  0.0   0:00.53 pdflush
  119 root      15   0     0    0    0 S  0.0  0.0   0:10.91 pdflush    
```
You can also use the ps command:
```
ps -ef | grep foo
```
will find processes run in the name of foo

I suggest you want to look for both a program called foo, and the foo-lish program that is trying to tell you that foo is giving you some hard work. I don't know what this program would be called - you'll need to look through top, it shoud show up somewhere near the top when you encourage it to talk to you by opening another app.

If there isn't a program running called foo, but there is some watchdog type program that is giving you the information, then maybe that program is badly configured. foo is often used as an arbitrary example file name, meaning that it is less likely to show up 'real life'. 

You can use the kill command to stop a process:
```
kill foo
```stops foo
remember:
```
ps -ef | grep foo
```
has it gone? If not,
```
kill -9 foo
```kill's it 'harder'

---


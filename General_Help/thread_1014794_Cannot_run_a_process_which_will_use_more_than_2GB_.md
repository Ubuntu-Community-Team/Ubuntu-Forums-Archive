---
title: "Cannot run a process which will use more than 2GB of memory after latest upgrade"
date: 2008-12-18
forum: General Help
---

### Post by erlenddavidson on 2008-12-18
I have a workstation with 8GB ram and swap.  I used to be able to run Vasp (a molecular dynamics code) and allow it to take lots of RAM.  After the upgrades from the last two days it crashes after the memory usage passes 2GB.

I am runnning *exactly* the same job as two days ago (same input file).

I am running the 64-bit version of ubuntu.

```

# uname -m
x86_64

# ulimit -a
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 71168
max locked memory       (kbytes, -l) 32
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 71168
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited

```

---


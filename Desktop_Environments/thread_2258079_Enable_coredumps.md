---
title: "Enable coredumps"
date: 2014-12-24
forum: Desktop Environments
---

### Post by nibal on 2014-12-24
I use Ubuntu 14.04 x64. I am a developer & admin and need to enable coredumps.  
I set soft and hard limits for "*" in /etc/limits.conf, but it doesn't seem to work.:(
Unfortunately these things they keep changing with every distro...
How can i enable them?

TIA,
Nikos

---

### Post by steeldriver on 2014-12-24
I've only ever done it via the bash shell's ulimit

```

ulimit -c unlimited

```

You can check the current ulimits with 'ulimit -a'

```

$ ulimit -a
core file size          (blocks, -c) unlimited
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 23952
max locked memory       (kbytes, -l) 64
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 23952
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited

```

For additional info, type 

```

help ulimit

```

at the shell prompt.

---

### Post by nibal on 2014-12-24
It worked. ty so much;-)

---


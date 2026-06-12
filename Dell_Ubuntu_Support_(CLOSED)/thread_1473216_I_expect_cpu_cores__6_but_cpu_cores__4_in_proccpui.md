---
title: "I expect cpu cores : 6 but cpu cores : 4 in /proc/cpuinfo (Dell T510, X5660 X 2 cpu)"
date: 2010-05-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Sanghee Kim on 2010-05-05
Dear.

My Lab bought Dell T510, Intel Xeon X5660 (6 core X 2). After install Ubuntu 9.04 server, I can find following information.

```

$ vi /proc/cpuinfo
...
model name      : Intel(R) Xeon(R) CPU           X5660  @ 2.80GHz
stepping        : 2
cpu MHz         : 2800.115
cache size      : 12288 KB
physical id     : 1
siblings        : 4
core id         : 0
cpu cores       : 4
...
$ uname -a
Linux mint 2.6.28-18-server #60-Ubuntu SMP Fri Mar 12 05:41:54 UTC 2010 i686 GNU/Linux
$ grep CONFIG_NR_CPUS /boot/config-2.6.28-18-server
CONFIG_NR_CPUS=64

```

I can find only 4 core instead of 6 core for each CPU. I disabled Hyper Threading and VT in BIOS.

Do you have any idea?

---

### Post by The Fold on 2010-08-13
Did you ever find a solution to this?

I'm having the same problem with some T5500's on Ubuntu 8.04.

---

### Post by solamour on 2010-10-09
Try the following and see what you are getting. If CONFIG_NR_CPUS is set to 8, that's the max CPU the kernel will recognize.

```
$ grep CONFIG_NR_CPUS /boot/config-`uname -r`
```

Follow the instructions at "[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)" and rebuild your kernel. Make sure you set the following in the kernel configuration.

```
Processor type and features
   [ * ] Support for big SMP systems with more than 8 CPUs
   (12)  Maximum number of CPUs  <-- set it to 12

Kernel hacking
   [   ] Compile the kernel with debug info
```
__
sol

---


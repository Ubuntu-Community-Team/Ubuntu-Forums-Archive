---
title: "High i/o wait when copying file"
date: 2009-08-28
forum: Desktop Environments
---

### Post by tomcheng76 on 2009-08-28
Hi all :)
when copying file, huge cpu %wa harm desktop response (can up to 90% ...)

CPU: Core 2 Duo E8200
memory: 8GiB DDR2 800

```
$ uname -a
Linux bomber-C2D 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux
```

Here is my test
> $ sysctl vm/overcommit_memory vm/dirty_background_ratio vm/dirty_ratio vm/dirty_expire_centisecs vm/dirty_writeback_centisecs
vm.overcommit_memory = 0
vm.dirty_background_ratio = 5
vm.dirty_ratio = 10
vm.dirty_expire_centisecs = 3000
vm.dirty_writeback_centisecs = 500

$ dd if=/dev/zero of=/tmp/test.out bs=8192k count=256
256+0 records in
256+0 records out
2147483648 bytes (2.1 GB) copied, 18.5065 s, 116 MB/s

$ sysctl vm/overcommit_memory vm/dirty_background_ratio vm/dirty_ratio vm/dirty_expire_centisecs vm/dirty_writeback_centisecs
vm.overcommit_memory = 0
vm.dirty_background_ratio = 2
vm.dirty_ratio = 4
vm.dirty_expire_centisecs = 1500
vm.dirty_writeback_centisecs = 500

$ dd if=/dev/zero of=/tmp/test.out bs=8192k count=256
256+0 records in
256+0 records out
2147483648 bytes (2.1 GB) copied, 22.5469 s, 95.2 MB/s


It seems the second one is lower iowait but slower transfer.

What should i do in order to increase the desktop responsiveness ?
firefox is :( slow when i am copying file ....
I don't mind slow transfer but please..how to do multiple task...
hey men, i have dual core cpu but i cant do anything else if i am copying many file...

Thanks in advance.

---

### Post by tomcheng76 on 2009-08-29
bump

thanks

---

### Post by kmccormick on 2009-09-18
More of a workaround than a solution, but there's a command-line utility called ionice which lets you set the priority for I/O on a process.

Should be installed already, but just in case: sudo apt-get install util-linux

Use when starting: $ ionice -c3 <command>

Use after already started: $ ionice -c3 -p<process id>

---


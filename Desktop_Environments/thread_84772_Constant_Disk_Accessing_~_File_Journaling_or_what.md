---
title: "Constant Disk Accessing ~ File Journaling or what?"
date: 2005-10-31
forum: Desktop Environments
---

### Post by ULffuntu on 2005-10-31
Hello,

I'm trying to track down a small constant disk access that occurs every 5 seconds. I don't think it is ext3 FS Journaling because I've set the partition to noatime,nodiratime and set the journal to data_writeback. It still happens.

When I went into the kernel in recovery mode (rc1) this disk activity ceased. So maybe this a process or could this be some sort of system logging activity? I removed the syslog.conf but it still happened at rc5. Thanks in advance for any expert help.

---

### Post by dbott67 on 2005-10-31
I'm definitely not an expert, but you could run 'top' from the command line and just watch the processes for CPU and memory usage.  It may give you an indication of the process that is respoonsible.

-Dave

---


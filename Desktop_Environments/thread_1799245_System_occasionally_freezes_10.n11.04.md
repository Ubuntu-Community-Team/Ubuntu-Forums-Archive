---
title: "System occasionally freezes 10.n/11.04"
date: 2011-07-07
forum: Desktop Environments
---

### Post by lister171254 on 2011-07-07
I'm now on 11.04 (64 bit on a desktop), but had the problem on 10 as well.

I get the occasional complete system freeze. There is nothing in the logs indicating a problem and it is not the graphics card, as I cannot ssh in from another machine. It sometimes happens after three days of running and sometimes after 20 hours.

I'd appreciate any suggestions/ideas.

---

### Post by wildmanne39 on 2011-07-07
> **lister171254 said:**
> I'm now on 11.04 (64 bit on a desktop), but had the problem on 10 as well.

I get the occasional complete system freeze. There is nothing in the logs indicating a problem and it is not the graphics card, as I cannot ssh in from another machine. It sometimes happens after three days of running and sometimes after 20 hours.

I'd appreciate any suggestions/ideas.
Hi, here is link on freezing, and also might not be a bad idea to clean out your computer it could be running warm, or possibly leaving it on that long it runs low on memory. 
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by lister171254 on 2011-07-07
Thanks for the link; I'll check it out.

Don't think it's temperature related as I have a watercooled system plus smart warning enabled. 

I suspect it may be I/O related (it happend at least twice while a full system backup was running), but have no way of proving this. The snippet shows that when it hang, it didn't flush the last message(s) to syslog as the log entry for the restart of the system is on the same line as the time entry when the system froze.

-------------------------
Jul  7 16:17:03 LeosLinux CRON[21690]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  7 16:19:Jul  7 17:05:51 LeosLinux kernel: imklog 4.6.4, log source = /proc/kmsg started.
-------------------------------

---

### Post by lister171254 on 2011-07-07
I've had a look at the link, but it seems to only address GPU problems.

As indicated in my initial post, I cannot ssh into the system when this happens.

---

### Post by svenakela on 2012-04-11
I know this is an old thread, but to whom it may concern...
I also experienced a lot of freezing and I addressed to a graphics card driver versus kernel issue.
Instead of using Unity 3D I changed to Unity 2D, there's no difference in look and feel but all the freezes are now gone. 3D applications still work as expected.

---


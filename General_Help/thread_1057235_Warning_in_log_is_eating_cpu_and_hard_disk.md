---
title: "Warning in log is eating cpu and hard disk"
date: 2009-02-01
forum: General Help
---

### Post by booyabazooka on 2009-02-01
Ubuntu 8.04, fully updated.

Dell Latitude D630

dmesg output:

```

[  824.263556] WARNING: at /build/buildd/linux-2.6.24/debian/build/custom-source-rt/drivers/net/wireless/b43/dma.c:1290 b43_dma_handle_txstatus()
[  824.263564] Pid: 23, comm: sirq-tasklet/1 Tainted: P        2.6.24-23-rt #1
[  824.263568] 
[  824.263569] Call Trace:
[  824.263593]  [<ffffffff8841de03>] :b43:b43_dma_handle_txstatus+0x433/0x470
[  824.263630]  [<ffffffff8841a677>] :b43:b43_debugfs_log_txstat+0x37/0xd0
[  824.263662]  [<ffffffff8840a443>] :b43:b43_interrupt_tasklet+0x343/0x7f0
[  824.263689]  [<ffffffff802469d7>] __tasklet_action+0x87/0x140
[  824.263702]  [<ffffffff802473d1>] ksoftirqd+0x121/0x2a0
[  824.263717]  [<ffffffff802472b0>] ksoftirqd+0x0/0x2a0
[  824.263728]  [<ffffffff802472b0>] ksoftirqd+0x0/0x2a0
[  824.263740]  [<ffffffff8025778b>] kthread+0x4b/0x80
[  824.263752]  [<ffffffff8020d3c8>] child_rip+0xa/0x12
[  824.263784]  [<ffffffff80257740>] kthread+0x0/0x80
[  824.263792]  [<ffffffff8020d3be>] child_rip+0x0/0x12
[  824.263803] 

```

This message is being printed constantly.

/var/log/syslog had expanded to ~5 gig before filling my disk (I have truncated it as a temporary fix).

htop reveals that

```
/bin/dd bs 1 if /proc/mksg of /var/run/klogd/kmsg
```

is using a significant amount of cpu time.

Disabling wireless makes the warnings stop.

Help?

---

### Post by booyabazooka on 2009-02-01
I've resorted to revoking write permissions on

    /var/log/messages
    /var/log/syslog
    /var/log/kern.log

to keep my disk from filling up.

But the dd process is still working overtime, constantly copying these useless warnings.

So, I killed this process.

Surely there's a better way to disable this excessive logging?

---

### Post by booyabazooka on 2009-02-06
Sorry to bump, but I just deleted 18 gigabytes of log files (kern, syslog, and messages seem to each cap out at 6 gig).  Frustrating.

Seems to be related to this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286285](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286285)

which makes me feel good that my pain is shared, but doesn't seem to help me find a workaround...

---

### Post by MarblePanther on 2009-02-06
> **booyabazooka said:**
> Sorry to bump, but I just deleted 18 gigabytes of log files (kern, syslog, and messages seem to each cap out at 6 gig).  Frustrating.

Seems to be related to this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286285](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286285)

which makes me feel good that my pain is shared, but doesn't seem to help me find a workaround...


"***Important summary for those experiencing this bug***
Kernel versions where this bug is fixed:
1) 2.6.27-10 from intrepid-proposed

Kernel versions where this bug is NOT fixed (if you are running one of these, please upgrade to known working kernel):
1) 2.6.27-7 from intrepid
2) 2.6.27-9 from intrepid-updates and intrepid-security

If you are experiencing this bug, please remove the linux-backports-modules packages too, as they don't contain a fix"

---

### Post by booyabazooka on 2009-02-06
Thanks for the response.  Does that mean I need to switch to Intrepid to fix this?

I'm currently running Hardy, 2.6.24-23-rt.

---

### Post by MarblePanther on 2009-02-06
> **booyabazooka said:**
> Thanks for the response.  Does that mean I need to switch to Intrepid to fix this?

I'm currently running Hardy, 2.6.24-23-rt.

Hmmm, I believe so.  I'm not sure what the latest kernel for Hardy is.  Upgrading to intrepid will *certainly* give you the fixed kernel.

EDIT:  Yes, you will have to upgrade to Intrepid and update fully.

I suggest you backup all your files to another harddrive and update to intrepid through update-manager.

---

### Post by booyabazooka on 2009-02-09
I upgraded, am on 2.6.27-11-generic, and the problem seems to be fixed.  Thanks for your help.

---

### Post by MarblePanther on 2009-02-09
I've also got a Latitude D630, glad i upgraded to Intrepid a while ago!  Glad you got it fixed.

---

### Post by paxmark1 on 2009-02-11
Sorry to rain on parade, but this bug is eating up cpu cycles for me and I am current.  It started several days ago when I did aptitude update and upgrade on 8.10.

Any other ideas?

Besides, telling to go from 8.04 to 8.10 is not a valid fix.  8.04 should still be supported.

---

### Post by MarblePanther on 2009-02-12
> **paxmark1 said:**
> Sorry to rain on parade, but this bug is eating up cpu cycles for me and I am current.  It started several days ago when I did aptitude update and upgrade on 8.10.

Any other ideas?

Besides, telling to go from 8.04 to 8.10 is not a valid fix.  8.04 should still be supported.

8.10 has the kernel with the fix by default after updates.  It is valid.

---

### Post by kvutza on 2009-02-14
8.04 is LTS, it means it is stable and supported. Advices to move away off it are _not_ valid answers. Definitely.

---

### Post by MarblePanther on 2009-02-14
> **kvutza said:**
> 8.04 is LTS, it means it is stable and supported. Advices to move away off it are _not_ valid answers. Definitely.

Kvutza, I am aware of that :roll:

Neither of you seem to understand.

The kernel he needs with the fix is the one included with Intrepid *not* Hardy.

It is not fixed in Hardy.

IT IS VALID

<now unsubscribing to this thread>

---

### Post by mateolan on 2009-08-04
I am experiencing this error on Jaunty and AMD64 chipset.  Should I revert to Inrepid?

---


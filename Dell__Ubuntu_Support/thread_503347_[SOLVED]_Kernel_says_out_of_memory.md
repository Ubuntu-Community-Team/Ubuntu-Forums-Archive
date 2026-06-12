---
title: "[SOLVED] Kernel says out of memory"
date: 2007-07-17
forum: Dell  Ubuntu Support
---

### Post by xluryan on 2007-07-17
Hey all. My computer keeps crashing. Ubuntu 7.04 // Dell Inspiron 5100 // ATI 32mb Radeon Mobility // 768mb RAM. After about 2-3 days of leaving it alone, I always walk in the room to find it sitting there with a black screen, fans spinning, and *totally* unresponsive to anything aside from holding down the power button.

I finally found out what happens when it jumps into that state. This was in my system.0 log file:

```

Jul 14 15:53:06 freedom kernel: [179239.898663] mapping-daemon invoked oom-killer: gfp_mask=0x201d2, order=0, oomki
lladj=0
Jul 14 16:03:41 freedom kernel: [179239.898729]  [out_of_memory+373/432] out_of_memory+0x175/0x1b0
Jul 17 17:41:17 freedom syslogd 1.4.1#20ubuntu4: restart.
```

The last line is from the hard reset I did to my laptop when I found it. What should I do to stop it from crashing?

---

### Post by az on 2007-07-17
> **xluryan said:**
> Hey all. My computer keeps crashing. Ubuntu 7.04 // Dell Inspiron 5100 // ATI 32mb Radeon Mobility // 768mb RAM. After about 2-3 days of leaving it alone, I always walk in the room to find it sitting there with a black screen, fans spinning, and *totally* unresponsive to anything aside from holding down the power button.

I finally found out what happens when it jumps into that state. This was in my system.0 log file:

```

Jul 14 15:53:06 freedom kernel: [179239.898663] mapping-daemon invoked oom-killer: gfp_mask=0x201d2, order=0, oomki
lladj=0
Jul 14 16:03:41 freedom kernel: [179239.898729]  [out_of_memory+373/432] out_of_memory+0x175/0x1b0
Jul 17 17:41:17 freedom syslogd 1.4.1#20ubuntu4: restart.
```

The last line is from the hard reset I did to my laptop when I found it. What should I do to stop it from crashing?

Are you running anything that is particularly memory-intensive?

Also you can let it run for a few days, but periodically check to see what it eating up the ram.  You probably have an application that has a memory-leak.  That would be a bug.

---

### Post by xluryan on 2007-07-18
Ok, I'll check it over the next few days. What's the best way to check it? The 'top' command?

---

### Post by az on 2007-07-18
Yes.  You can also put the system monitor applet on your panel and then click on it - that gives you the list of running processes and how much cpu and ram they are using.

---

### Post by xluryan on 2007-07-18
I got it. It was gDesklets...

From top I sorted the output by memory usage, and the command "python" was increasing at about 1% memory usage every 20 minutes (estimate). I did a calculation which said that python would be at 100% in 33 hours total time. Sounds about how often my computer would crash.

To find out that that specific instance of python was gDesklets I ran the command "ps axjf", then scrolled down to find the PID that matched "python" from top. It pointed to the binary for gDesklets.

Just to test and make sure it was in fact gDesklets, I closed gDesklets and sure enough the "python" entry from top dissappeared, and running "free -m" showed about 300 more free MB's of RAM instantly.

So now I've disabled a few of my desklets. I'll let this run for a bit and check back in a few hours or so.

Just for info, the desklets I was running were ExternIP and some binary clock one (can't remember the name). I've closed the binary clock, and I'm hoping the little external IP display won't steal all my RAM. Guess I'll find out in a few hours...

Thanks for all your posts!

---

### Post by tgalati4 on 2007-07-18
I doubt the binary clock was creating a memory leak, but you will find out soon enough.

---

### Post by xluryan on 2007-07-18
Well that seems to have done it. The python command for my gDesklets is staying at 2.7% memory usage after several hours. All I've done is turned off the single desklet. I'm still running the ExternIP desklet with no problems.

I'll post back if anything changes, but for now it looks like I'm in the clear :)

---


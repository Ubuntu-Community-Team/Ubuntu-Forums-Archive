---
title: "Ubuntu 8.10 and nano/microsecond resolution for select() and poll()"
date: 2008-12-07
forum: General Help
---

### Post by JohnVM on 2008-12-07
Hey Guys,

I'm a fairly newb Ubuntu user, and I'm a software developer. I've been experiencing some odd behavior in one of my applications. It uses a select() w/ resolution of 1ms. After trying to troubleshoot this issue, I stumbled across the following kernel mailing list message:

[http://lkml.indiana.edu/hypermail/linux/kernel/0808.3/2216.html](http://lkml.indiana.edu/hypermail/linux/kernel/0808.3/2216.html)

I've included a quote of the mail below to save people having to click links (although there's more information/other emails there if you do click).

After reading up on this, it looks like this could be the cause of my issues. I was wondering if this patch would ship with Ubuntu 8.10 by default (as it's part of the kernel now as that's the kernel mailing list?), or if I have to do something to enable/get this patch. If I do have to do something, what exactly is it that I have to do?

Sorry for the newbness.

- jm

> 
**[patch 0/5] Nano/Microsecond resolution for select() and poll()**

Today in Linux, select() and poll() operate in jiffies resolution
(granularity), meaning an effective resolution of 1 millisecond (HZ=1000) to
10 milliseconds (HZ=100). Delays shorter than this are not possible, and all
delays are in multiples of this granularity.

The effect is that applications that want (on average) to specify more
accurate delays (for example multimedia or other interactive apps) just
cannot do that; this creates more than needed jitter.

With this patch series, the internals of select() and poll() interfaces are
changed such that they work on the nanosecond level (using hrtimers). The
userspace interface for select() is in microseconds, for pselect() and
ppoll() this is in nanoseconds.

[actual behavior obviously depends on what resolution the hardware timers work, on
modern PCs this is pretty good though]

To show this effect I made a test application to measure the error made
in the select() timing.

For example, a userspace application asking for a 1200 microsecond delay, on
a HZ=1000 kernel, will in practice get a 1997 microsecond delay, a delta of
almost 800 microseconds (which is of course a high percentage of 1200). The
extreme case is asking for 1 microsecond, and getting 998 microseconds
delay... with the patch we get a 250 times improvement in behavior (!).

A graph of various inputs with the jitter can be seen at
[http://www.tglx.de/~arjan/select_benefits.png](http://www.tglx.de/~arjan/select_benefits.png)

One thing to note is that on my machine, the current select() implementation
will return after 1997 microseconds when asked for 1999 microseconds; this
can be seen in a zoom in of the graph above:
[http://www.tglx.de/~arjan/zoom.png](http://www.tglx.de/~arjan/zoom.png)
E.g. select() is returning too early in current Linux kernels; and this is
also fixed (by nature) by this patch series.
In the graph there's a 4 microsecond delta for most data points, this is
basically the measurement overhead (C-state exit, a few system calls, a
loop and some math).


About the patches:

Patch 1: Introduces infrastructure where select() and poll() start tracking
the end time in a "struct timespec" rather than in jiffies, so in
nanosecond resolution.
Patch 2: Uses the now available end time in nanoseconds to calculate at the
end of a select()/ppoll() how much time is left and returns this
in a high resolution rather than jiffies granularity
Patch 3: Introduces a schedule_hrtimeout(); a high resolution version of the
equivalent schedule_timeout() function.
Patch 4: Converts over select() to schedule_hrtimeout()
Patch 5: Converts over poll() to schedule_hrtimeout()


Note:
even though poll() (as opposed to ppoll()) only accepts milliseconds
as userspace interface, the behavior will still improve because the current
time no longer needs to be rounded up to the next jiffie, so on average
a 500 milliseconds behavior improvement.

Note 2:
I'm a bit unsure about the restart code and how that works; I'd like to
request a bit of help on figuring out how that code is supposed to work.

Future work:
I'd like to get rid of the jiffies timeout entirely over time, and
only use hrtimers (makes the code a lot nicer) but that's for now
a separate step, first I'd like to see how this change pans out.



H

---


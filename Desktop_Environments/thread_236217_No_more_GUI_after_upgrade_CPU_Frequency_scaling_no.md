---
title: "No more GUI after upgrade: CPU Frequency scaling not supported"
date: 2006-08-14
forum: Desktop Environments
---

### Post by renebe on 2006-08-14
I have a pc with an AMD Sempron 3400+ processor. I installed Ubuntu 5.10  on this machine from cd. Through the Internet I updated my Ubuntu 5.10.

That worked fine.

I also have a pc with a Pentium 4 processor. On that machine I also installed Ubuntu 5.10 from cd, and I also updated trhough the Internet.

That worked fine too.

Now I upgraded my Pentium 4 pc, again though the Internet, to Ubuntu 6.06. To complete satisfaction: it runs like a charm.

I tried to do the same to my AMD pc: I upgraded it to Ubuntu 6.06. That went wrong: I can no longer start any GNOME sessions. I suspect it may have something to do with the following error message I get:

    CPU Frequency scaling not supported

There's also another message that might have something to do with it:

    udevd-event[3307]: wait_for_sysfs:
    waiting for '/sys/devices/platform/i82365.0/bus' failed

When I still had 5.10 on this AMD-pc, everything worked fine: I was able to start GNOME-sessions with no problems whatsoever. But after the upgrade I could no longer do that. Anyone have any idea as to what went wrong and how to fix this problem?

I did some Googling, and found only few hits. I saw some people speak about powersaved and powernow, but that didn't help me any further.

Sincerly,
René.

---

### Post by renebe on 2006-08-14
After I did some puzzling, I found the following:

The problem of not being able to start a GNOME-session, was not caused by one (or both) of the errors I mentioned above.

When I log in into the Failsafe Terminal, and su too root, I could start a GNOME-session without any trouble, just by typing startx.
If I try to do the same als rene (my user-id), it won't start. It said:

    xauth: Creating new authority file /home/rene/.serverauth.4940
    xauth: /home/rene/.Xauthority not writable, changes will be ignored
    xauth: error in locking authority file /home/rene/.Xauthority
    xauth: error in locking authority file /home/rene/.Xauthority
    xauth: error in locking authority file /home/rene/.Xauthority

    X: user not authorized to run the X server, aborting.
    giving up.

That makes sense, because the owner of /home/rene/.Xauthority turned out to be root. When I look at my P4 pc, that does it the way it should, the owner is rene. So something seems to be broken by the upgrade?

I tried chown-ing .Xauthority aan te passen, but my problem persists.

Anybody any clues?

Thanx,
René.

---


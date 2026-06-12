---
title: "How to REALLY enable ntp time synchronization?"
date: 2005-01-21
forum: Desktop Environments
---

### Post by istoyanov on 2005-01-21
Until now I was thinking that when installing ntp-simple and putting the appropriate check-marks in the ``Adjust Date&Time'' dialogue, my system clock gets synchronized by the preferred time server.

Well, as I already said: UNTIL NOW I WAS THINKING SO!!!

Recently I installed Ubuntu on another box in the lab, and after a day or two, I noticed that both clock display not the same time:(

I did some research, and found that one could check if the clock is being updated, by issuing the command
```

ntpq -pn

```

Here's what I get:
```

     remote           refid      st t when poll reach   delay   offset  jitter
=============================================================================
 80.127.4.179    .INIT.          16 u    -   64    0    0.000    0.000 4000.00
 82.228.182.88   .INIT.          16 u    -   64    0    0.000    0.000 4000.00
 66.115.130.4    .INIT.          16 u    -   64    0    0.000    0.000 4000.00

```
The  corresponding (modified according the recommendations found at [http://www.pool.ntp.org](http://www.pool.ntp.org)) /etc/ntp.conf is:
```

driftfile /var/lib/ntp/ntp.drift
statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable

server  0.pool.ntp.org
server  1.pool.ntp.org
server  2.pool.ntp.org

```

I learned that you haven’t got proper synchronization when all the remote servers have jitters of 4000 with ``delay'' and ``reach'' values of zero, as it is in my case.

Does anybody know what I have to do, in order to REALLY have my clock in sync?

I have some doubts that perhaps my ports are blocked somehow, but I have really NO experience at all with this matter, so I would be very happy if someone could help me to resolve this issue.

All the best!

---

### Post by mendicant on 2005-01-21
I have the packages ntp, ntp-simple and ntp-server installed and it works for me.  If you haven't let it run for very long, ntpq -pn will show INIT for each server.

Also check out:
[http://www.eecis.udel.edu/~mills/ntp/html/debug.html](http://www.eecis.udel.edu/~mills/ntp/html/debug.html)

---


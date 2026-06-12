---
title: "Spin down of hard drives"
date: 2006-09-02
forum: Desktop Environments
---

### Post by lozenge on 2006-09-02
Can I, in Ubuntu, set a time limit that the drives stay active for? I know in Windoze I could set spindown to ten minutes or so to save their life for a bit, is it possible at all in Ubuntu?

Thanks.

---

### Post by jpkotta on 2006-09-02
Yes you can.  I honestly don't recommend it.  It's really not good for drives to spin down and up all the time.  I run my desktop continuously; I reboot about once every 6 weeks and I've had essentially no hardware problems with it (about 33 months).  My family computer, on the other hand, once had its harddrive set to spin down after an hour of inactivity, and it has died (clearly, it's not set that way anymore).  For laptops, you can set it to spin down to save power, but again, it may not be worth it.  Hard drives use *a lot* more power to spin up than to just keep spinning.  High end drives used in servers often have a feature to make sure that not all of the drives running off of the same power source spin up at the same time, otherwise the power supply may be overloaded.  

With all of that out of the way, use the hdparm command:
```
sudo hdparm -S <number> <device>
```
where <number> is an integer from 0 to 255.  The mapping from <number> to time is complicated:
> The encoding of the timeout value is somewhat peculiar.  A value of zero
              means "timeouts are disabled": the device will not automatically enter standby mode.  Values from 1  to
              240 specify multiples of 5 seconds, yielding timeouts from 5 seconds to 20 minutes.  Values from 241 to
              251 specify from 1 to 11 units of 30 minutes, yielding timeouts from 30 minutes to 5.5 hours.  A  value
              of 252 signifies a timeout of 21 minutes. A value of 253 sets a vendor-defined timeout period between 8
              and 12 hours, and the value 254 is reserved.  255 is interpreted as 21 minutes plus 15  seconds.   Note
              that some older drives may have very different interpretations of these values.


<device> is your hard drive's name in /dev/, e.g. /dev/hda.

---


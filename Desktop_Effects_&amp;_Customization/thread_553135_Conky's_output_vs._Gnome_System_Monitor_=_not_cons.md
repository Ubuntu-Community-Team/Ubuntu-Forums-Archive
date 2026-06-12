---
title: "Conky's output vs. Gnome System Monitor = not consistent?"
date: 2007-09-17
forum: Desktop Effects &amp; Customization
---

### Post by timzak on 2007-09-17
I noticed that Conky's output for memory usage by processes doesn't line up with what System Monitor says for the same processes in Feisty.  It seems like the Conky results are always higher than System Monitor's.  For example, Conky reported Firefox using about 5% of my 1 GB of ram = about 50 MB.  But System Monitor was reporting that Firefox was using 38 MB.

Is there an explanation for this inconsistency?  Is one more "right" than the other?

Thanks in advance.

---

### Post by kevdog on 2007-09-18
I believe conky's sampling interval is quite small, whereas the system monitor gives an average over 1 minute.  I am noticing however in the resources tab in system monitor that has a very small sampling period, that the results tend to compare nearly equal to conky.

---

### Post by timzak on 2007-09-18
Thanks for the reply.  I'll check out the resources tab when I get a chance (I'm on a Windows PC right now) and see if my system jives with what you're saying.

---

### Post by notwen on 2007-09-18
I compared these a month-ish back or so and my conky and system resources were nearly identical. Generally within 5% of each other for application memory and cpu usage.  How often do you have your conky updating?

---

### Post by timzak on 2007-09-18
> **notwen said:**
> I compared these a month-ish back or so and my conky and system resources were nearly identical. Generally within 5% of each other for application memory and cpu usage.  How often do you have your conky updating?

I believe it's set up update every 3 seconds.

---

### Post by timzak on 2007-09-19
Yep, the resources tab shows identical memory usage to conky.  It's just the processes tab that shows differences.  Currently conky shows Firefox at 61MB, while the processes tab shows 48MB.  Beryl is using 46MB according to conky and 39MB according to the processes tab.  So something is off somewhere, but the sum of both are equal.  I was just curious if anyone knew any more about this.

Thanks for the replies.

---


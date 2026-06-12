---
title: "Extremely high disk IO"
date: 2009-04-29
forum: General Help
---

### Post by pablo2dot0 on 2009-04-29
Since I upgraded to Jaunty I have seen several times my system going nuts, the system will start reading from disk non stop and the system will become unusable for a while, most of the times it simply won't come back and I'll have to reset.

vmstat shows that the IO is exclusively reading.

At one point I stopped everything that could cause this, prelink, firefox, cron, openoffice, etc., every user app that could be running (other than minimal gnome) was either killed or SIGSTOPped, but this kept happening anyway, I could see how after stopping everything the reading would stop but after a while it just resumed and sent the load back to the 2xs.

I haven't experienced this before Jaunty and I have seen this happen at least three times a day since my upgrade.

Has anyone experienced something similar?

I noticed an error in dmesg regarding read ahead, unfortunately I had reinstalled since then so I can't show it. BTW, I was using reiserfs before and now I'm using ext4.

---

### Post by iponeverything on 2009-04-29
next time it happens, open a terminal and run "top"

---

### Post by pablo2dot0 on 2009-04-30
I've done that, nothing appears to be trying to read that much data.

---


---
title: "suspend / hibernate problem in Lucid (e6400)"
date: 2010-07-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Am Elder on 2010-07-21
Hello all.  Can anyone help me?  I run Ubuntu Lucid on my Dell E6400  laptop with an nvidia gpu, using the proprietary driver.

When I click Suspend or Hibernate, instead of suspending or hibernating,  the display goes to sleep. Then when I press a key or touch the trackpad,  the Log On dialog box appears.  This problem appeared in autumn last  year after I had been running Jaunty for several months. This spring, I  updated to Karmic and then straight through to Lucid and the problem  remains.

I've attached a text file with the last two log reports from my  /var/log/pm-suspend.log.  One records me trying to suspend, the second  trying to hibernate.

It looks to my untrained eye that the important lines in both cases are:
```
/usr/lib/pm-utils/sleep.d/98tuxoniceui suspend  suspend:/usr/lib/pm-utils/sleep.d/98tuxoniceui: 10: cannot create  /sys/power/tuxonice/user_interface/enable_escape: Directory nonexistent
Returned exit code 2.
Thu Jul 22 04:47:58 CEST 2010: Inhibit found, will not perform  suspend
```It looks to me like my computer is trying to use tuxonice  to suspend. However, using synaptic, I've found the only tuxonice  package installed on my computer is tuxonice-userui, which according to  the description doesn't contain the working parts.  I also can't find  another tuxonice package in the Lucid repository. 

**Update: **Now, I've found tuxonice installed as part of the pm-utils package, so it's not a matter the utility not being installed, but it seems to be configured incorrectly.

  Can anyone help me figure out how to fix this?

---


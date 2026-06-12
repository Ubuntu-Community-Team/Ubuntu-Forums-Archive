---
title: "System time keeps jumping ahead on Jaunty"
date: 2009-05-23
forum: General Help
---

### Post by csete on 2009-05-23
I have a Jaunty server and laptop.  The laptop is holding time just fine, but the server keeps jumping ahead and it seems to be somewhat random.  For instance, it says 6:08pm right now even though it is actually 4:39pm right now.  According to the user interface settings, I am using ntp to update the clock and it is set to use US Central timezone.  I have no idea where to look to figure out why this keeps happening.  Does anyone have any thoughts?

Thanks,
Craig

---

### Post by Kareeser on 2009-05-23
It sounds like the hardware clock isn't set properly. Whenever Ubuntu reboots, it syncs the system clock with the onboard clock, which would explain why the time is always ahead whenever you reboot.

First, run ntpdate to synchronize:
```
sudo ntpdate time.nist.gov
```

Then synchronize the system clock to the hardware clock:
```
hwclock --systohc
```

If you continue to run into this problem, check firstly to make sure your locale and time zone is set correctly.

Otherwise, you may have a faulty CMOS battery.

---

### Post by csete on 2009-05-24
Thanks for the ideas.  I've run those commands and now I will have to watch to see if the time holds.  This is a home server machine, so it is rarely rebooted and I'm not sure that the battery comes into play at that point?  I wasn't seeing any problem prior to the Jaunty upgrade, either.

If I need to check the timezone settings and such, where can I look outside the UI?  Is there a command-line tool for interacting with that?

Thanks again,
Craig

---

### Post by csete on 2009-05-25
Unfortunately, the time is off again.  Strangely, it appears to be happening overnight.  I have two cron jobs that run at midnight and 5am overnight.  According to my email received for those cron jobs, they occurred at the correct time.  But, looking at the time on the machine, I can see the time is now 37 minutes ahead of real time.  It seems like somehow this may be related to the ntp updates going awry.  

Can anyone else offer any thoughts?  I'm going to try to disable ntp updates for the moment and see if it holds time better for the moment.  If so, I at least have a culprit to dig into further.

Any other thoughts greatly appreciated.

---


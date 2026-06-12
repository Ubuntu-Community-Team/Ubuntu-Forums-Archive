---
title: "Spontaneous Reboot"
date: 2009-04-08
forum: General Help
---

### Post by Tteddo on 2009-04-08
This is odd, got up this morning and my computer was at the login screen. It had rebooted at 03:22. I thought Ubuntu didn't do that (i.e. forced reboots)?
All I see in the syslog is:
> Apr  8 03:22:21 Arrakis syslogd 1.5.0#1ubuntu1: restart.
Is there somewhere else I can look to find out why it did that? I am behind a router and there's no one here but me, so it did it on it's own for sure.

---

### Post by Sam Lars on 2009-04-09
You could look in the logs up until right before it rebooted... I think the message you're looking at marks the beginning of the boot.

---

### Post by Tteddo on 2009-04-09
That's the thing, the messages log looked like this for hours:
> Apr  8 03:12:10 Arrakis -- MARK --
Then this:
> Apr  8 03:22:21 Arrakis syslogd 1.5.0#1ubuntu1: restart.
The syslog looks like this:
> Apr  8 03:12:10 Arrakis -- MARK --
Apr  8 03:17:01 Arrakis /USR/SBIN/CRON[24911]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  8 03:19:56 Arrakis kernel: [563210.190400] NVRM: Xid (0005:00): 8, Channel 00000003
Apr  8 03:20:05 Arrakis kernel: [563218.175919] NVRM: Xid (0005:00): 8, Channel 00000003
Apr  8 03:20:09 Arrakis kernel: [563218.179888] NVRM: Xid (0005:00): 12, COCOD 0000001e 31415930 00000019 00000444 ff000000
Apr  8 03:22:21 Arrakis syslogd 1.5.0#1ubuntu1: restart.

 It just restarted like Windows machines sometimes do for updates.
I know the power was fine too.
Admittedly I don't know what those kernel messages mean....
Is there any reason that Ubuntu just up and decides it needs a reboot?

---

### Post by Sam Lars on 2009-04-09
Um... no, I though Ubuntu was more polite than that...

Do those NVRM: Xid (0005:00) messages appear anywhere besides right before the machine rebooted?

---

### Post by Tteddo on 2009-04-09
It appears on the 6th (the reboot was on the 8th) but it didn't reboot then. I didn't find it anywhere else going back 4 days except for those 2 spots. I just did a Google search for NVRM: Xid and it turns up when the video is being stressed. I wonder if one of the random screensavers caused it. But that should have just killed X, not caused a complete reboot, right?

---

### Post by Sam Lars on 2009-04-09
Usually, yes, it should just kill X.  I wouldn't completely rule out the possibility of a reboot, though.

---

### Post by English Oatcake on 2009-04-09
I once managed to completely crash X to a point where the system restarted - although I was in the process of testing a modification to the kernel for a project so I assumed that was the problem.

You could try your screensavers manually and find out if one of those is causing it to die, personally unless it starts doing it regularly or you are running time-lengthy processes I wouldn't worry about it

---

### Post by Tteddo on 2009-04-09
The thing is, it's been running for months with the random screensavers. I assume it's been through all of them multiple times. I do have a laptop (Acer) that crashes with the random savers, but never my main machine.
Is there a setting somewhere that will increase the level of detail in the syslog so maybe I could get more info on it?
I have been switching about 1 customer a week to Ubuntu for about 3 months, and I could see that being handy for other problems too.

---


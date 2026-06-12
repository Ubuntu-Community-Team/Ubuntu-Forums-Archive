---
title: "Desktop eventually just hangs"
date: 2022-04-04
forum: Desktop Environments
---

### Post by lister171254 on 2022-04-04
I'm running Ubuntu 21.10 as a Music server.

Everything works as expected as long as I'm actually using the box (i.e. play music), but if I stop for a period of time (not sure about the lenght) the box just 'hangs'.

I get the same behaviour if I boot the box, but don't log in; eventually it will just hang.

I have no explanation for this as there is nothing in the logs. Following are the last entries before it hangs; the lights are still on on the PC, but there is just no activity.

```
-- Journal begins at Sun 2020-10-18 14:23:38 AEDT, ends at Tue 2022-04-05 10:31:07 AEST. --
Apr 04 12:45:25 OurMusic1 systemd[1]: Starting Ubuntu Advantage Timer for running repeated jobs...
Apr 04 12:45:26 OurMusic1 systemd[1]: ua-timer.service: Deactivated successfully.
Apr 04 12:45:26 OurMusic1 systemd[1]: Finished Ubuntu Advantage Timer for running repeated jobs.
Apr 04 12:54:59 OurMusic1 smartd[1039]: Device: /dev/sda [SAT], SMART Usage Attribute: 190 Airflow_Temperature_Cel changed from 65 >
Apr 04 12:54:59 OurMusic1 smartd[1039]: Device: /dev/sda [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 35 to 33
Apr 04 12:55:00 OurMusic1 smartd[1039]: Device: /dev/sdb [SAT], SMART Usage Attribute: 190 Airflow_Temperature_Cel changed from 65 >
Apr 04 12:55:00 OurMusic1 smartd[1039]: Device: /dev/sdb [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 35 to 34
Apr 04 13:17:01 OurMusic1 CRON[1686]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 04 13:17:01 OurMusic1 CRON[1687]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 04 13:17:01 OurMusic1 CRON[1686]: pam_unix(cron:session): session closed for user root

```

---

### Post by TheFu on 2022-04-04
Check the *logind.conf* file to see if hibernation or standby modes are enabled.
That's the first place.
Next, I'd look for hardware failures - power spikes, bad cables. Once had a GPU that was failing, but not yet dead, causing system lockups.  This was after I'd already replaced the PSU for better one.

In short, ...
simplify and test.  Repeat.

Keep simplifying the setup (i.e. removing hardware and software), until the part causing the issue is removed/replaced.

There are lots of different logs too. Check them all.  Certainly check the music server software logs.

---


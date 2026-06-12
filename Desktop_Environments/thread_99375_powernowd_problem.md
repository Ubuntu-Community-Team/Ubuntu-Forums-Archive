---
title: "powernowd problem"
date: 2005-12-05
forum: Desktop Environments
---

### Post by Ronin_error on 2005-12-05
Using Dell Inspiron 8100
When I log into a console, this error comes up:

[4296902. 749000] cpufreq: changed failed with new_state 1 and result 0

----------------------------------------------------------------------------------------------------------
                                            System log

localhost kernel [4295636.265000] cpufreq: change failed with new_state 1 and result 0
localhost kernel [4295650.313000] cpufreq: change failed with new_state 1 and result 0
localhost kernel [4295667.160000] cpufreq: change failed with new_state 1 and result 0
localhost kernel [4295698.983000] cpufreq: change failed with new_state 1 and result 0
localhost anacron[7633] Job `cron.monthly' terminated
localhost anacron[7633] Normal exit (3 jobs run)
localhost kernel [4295762.189000] cpufreq: change failed with new_state 1 and result 0
localhost kernel [4295847.295000] cpufreq: change failed with new_state 1 and result 0
localhost kernel [4295861.424000] cpufreq: change failed with new_state 1 and result 0
localhost kernel [4295884.322000] cpufreq: change failed with new_state 1 and result 0
localhost kernel [4295922.652000] cpufreq: change failed with new_state 1 and result 0
localhost kernel [4296112.813000] cpufreq: change failed with new_state 1 and result 0
localhost kernel [4296902.749000] cpufreq: change failed with new_state 1 and result 0
localhost kernel [4297064.907000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
localhost kernel [4297064.907000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
localhost kernel [4297064.907000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
localhost /USR/SBIN/CRON[10781] (root) CMD (   run-parts --report /etc/cron.hourly)

---

### Post by migueljacq on 2005-12-05
Yep. This was filed as a bug, happens with most laptops, it's a speedstep error.

The solution is in this [thread]("http://ubuntuforums.org/archive/index.php/t-75598.html"): mjwood0's last post on the page. Just requires an edit of the powernowd file.

Cheers

---

### Post by Ronin_error on 2005-12-07
That did the trick, thanks for the help!

---


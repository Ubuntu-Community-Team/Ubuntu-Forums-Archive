---
title: "launcher for trim ssd"
date: 2018-01-12
forum: Desktop Environments
---

### Post by j3984 on 2018-01-12
how about terminal code to create a launcher that runs" fstrim -v / "
it would help...
thanks

---

### Post by DuckHook on 2018-01-12
You appear to be addressing the forums as if to the developers. The forums are made up of, and managed by, ordinary users like you and me. The developers rarely, if ever, visit.

As for your question, I believe that all current *buntu versions already run trim weekly. My Xenial install has:```
duckhook@Zeus:~$  ll /etc/cron.weekly
total 40
<snip>
-rwxr-xr-x   1 root root    86 Aug  4  2015 fstrim*
<snip>
```…of which the contents are:```
duckhook@Zeus:~$  cat /etc/cron.weekly/fstrim
#!/bin/sh
# trim all mounted file systems which support it
/sbin/fstrim --all || true
```

---

### Post by mc4man on 2018-01-12
fstrim needs to be run as root so if you're really inclined to create a desktop launcher (whatever.desktop) that runs a root command, I'm sure you can search out the few solutions to that.
Hardly seems worth the effort as it runs weekly anyway at least in 16.04 + ( I believe in 14.04 some ssd's were blacklisted, in many cases improperly..

Preferred here is to modify /ect/cron-weekly/fstrim to create a log entry everytime it runs. Then you can just check the log every once & a while to make sure it's been running,ect.
I change it to 
```
#!/bin/sh
LOG=/var/log/trim.log
echo "*** $(date -R) ***" >> $LOG
fstrim -v / >> $LOG
```
After editing /ect/cron-weekly/fstrim to above can be tested by running this & then see if log is properly created.
```
sudo run-parts /etc/cron.weekly -v
```

---

### Post by DuckHook on 2018-01-12
Thanks, *mc4man*! That's a cool suggestion &#8230;and very useful.

Does it get nerfed with the next update?

---

### Post by mc4man on 2018-01-12
> **DuckHook said:**
> Thanks, *mc4man*! That's a cool suggestion …and very useful.

Does it get nerfed with the next update?
No, I don't believe I've seen an update to whatever installs that cron script ever... (at least post release.
I guess one could also modify to do all mounted partitions instead of just /  though here I'm ok with a weekly on /  as my data partition doesn't really need & any other Os's  also runs same script themselves.

Edit:
Maybe that package has been updated though the modded script is still there in my 16.04 install though it's only 6 months old.
The package is util-linux, will have to test..
If I re-install util-linux it does not replace the cron file, can't say what an actual update would do...

---

### Post by QIII on 2018-01-12
You could put it in cron.daily.

Or you could create a job to do it hourly or every 5 minutes.

---


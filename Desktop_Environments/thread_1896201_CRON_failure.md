---
title: "CRON failure"
date: 2011-12-16
forum: Desktop Environments
---

### Post by JasonFWard on 2011-12-16
I setup Simple Backup today, and scheduled it to do backups every hour, something I've done successfully for a few years now.

But I could see it wasn't running.

I've dug into the logs for CRON and I see this

```
Dec 16 15:17:01 Penny CRON[20915]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 16 15:17:02 Penny CRON[20914]: (CRON) error (grandchild #20915 failed with exit status 1)
Dec 16 15:17:02 Penny CRON[20914]: (CRON) info (No MTA installed, discarding output)
```

Can someone explain to me what that means?  And where next I should look for the problem?

---

### Post by squaregoldfish on 2011-12-16
Can you run the backup script (from with /etc/cron.hourly) from a terminal, and see what the output is? It's throwing an error (that's the exit status 1) which isn't being logged for some reason.

If you run it from a terminal, you should be able to see why it's failing. (You may need to run it using sudo.)

Steve.

---

### Post by JasonFWard on 2011-12-16
Yeah have done some more digging, I tracked down sbackup's own logs and found it reports two problems

1) It can't talk to DBus
2) It can't mount a volume it seems it wants

At the moment I'm assuming (perhaps wrongly) that it can't mount the volume because it can't talk to DBus.

Why it can't talk to DBus I don't know, I'm asking about that [here](http://ubuntuforums.org/showthread.php?t=1896213).

---


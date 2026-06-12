---
title: "Massive GNOME error. Help would be GREATLY appreciated."
date: 2007-11-30
forum: Desktop Environments
---

### Post by FRuMMaGe on 2007-11-30
Out of nowhere, I have started recieving a gnome error whenever I log on.

```
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The Settings Daemon restarted too many times.

The last error message was:

System exception: IDL:Bonobo/GeneralError:1.0 : Couldn't spawn a new process:Failed to execute child process "/usr/lib/control-center/gnome-settings-daemon" (File too large)

GNOME will still try to restart the Settings Daemon next time you log in.
```

I assume the real problem is the "File Too Large" line. Apparently my gnome-settings-daemon is too big.

I have googled for hours but to no avail. What can I do?

---

### Post by mrgnash on 2007-11-30
Perhaps deleting everything under ~/.gnome and then restarting might have some effect.

---

### Post by Scruffynerf on 2007-11-30
Heh, I got the same error message upgrading to Gutsy. Much googling later, went back to Feisty.

Just wait 5 months or so for Hardy, the LTS. Gutsy's almost behaving (judging from these forums) like a beta or RTS release of what will be in Hardy.

---

### Post by igknighted on 2007-11-30
> **Scruffynerf said:**
> Heh, I got the same error message upgrading to Gutsy. Much googling later, went back to Feisty.

Just wait 5 months or so for Hardy, the LTS. Gutsy's almost behaving (judging from these forums) like a beta or RTS release of what will be in Hardy.

I think you are missing the point a bit...

1) That error is as old as the sun, it doesn't matter whether it is on Dapper, Edgy, Feisty or Gutsy.  A simple restart of gnome usually fixes it.

2) If you wait for hardy you will be just as disappointed.  The reason there are issues is because Gutsy is new and just out of beta/rc.  Hardy will have the same issues.  LTS means long term support... it doesn't say anything about stability from day 1.  The reason Dapper is the "stable one" now is because there have been bugs being worked out for two years (including the beta's).  I dunno if you were around back then, but when Dapper came out it was a disaster.  The same uproar from the community for minor bugs (which were patched) and all the same stuff you see... and on top of that, it was two months late (hence 6.06 not 6.04).  They even released an update to the CD (6.06.1) because the original had bugs.  So I highly doubt Hardy will be any better than Gutsy right away.

3) Gutsy might have issues, but if you recall, people hated Dapper, Edgy and Feisty in the first little while too.  So give it time, run all the updates when you install, and if you find a bug report it, because thats how they get fixed.

---


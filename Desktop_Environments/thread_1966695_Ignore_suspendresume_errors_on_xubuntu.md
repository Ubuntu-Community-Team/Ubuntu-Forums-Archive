---
title: "Ignore suspend/resume errors on xubuntu"
date: 2012-04-27
forum: Desktop Environments
---

### Post by ngagun on 2012-04-27
xubuntu 12.04 on a laptop...

When I suspend or resume, I see for about half a second a log of error messages (that are also written to syslog). I don't think the errors are serious, I would like not to see them. Is this possible?

After looking at the timing in syslog, I see that the errors happen each time I resume, not suspend:

Apr 27 06:33:52 computername kernel: [ 8282.658967] legacy_resume(): pnp_bus_resume+0x0/0x70 returns -19
Apr 27 06:33:52 computername kernel: [ 8282.658973] PM: Device 00:0a failed to resume: error -19

Apr 27 06:33:52 computername kernel: [ 8282.658967] legacy_resume(): pnp_bus_resume+0x0/0x70 returns -19
Apr 27 06:33:52 computername kernel: [ 8282.658973] PM: Device 00:0a failed to resume: error -19

Any idea what these are?

Or easier, how not to see them every time I suspend or resume?

---

### Post by JakeConnors on 2012-06-19
I have been having this same problem with 12.04 LTS lately. I have a Thinkpad T-400. Did you ever figure out what this issue was?

---

### Post by isosavi on 2012-08-08
I have exactly the same issue with Lenovo X301. And it happens every time during resume from suspend. I cannot activate hibernation at all.

---

### Post by Austin Texas on 2012-08-08
It is very easy to view your log files in 12.04 LTS
Open the Log File Viewer.

---

### Post by Toz on 2012-08-08
> **isosavi said:**
> I have exactly the same issue with Lenovo X301. And it happens every time during resume from suspend.

Hello isosavi and welcome to the forums.

Can you please confirm that your problem is the same - errant messages in syslog when suspending? If so, you can safely ignore them if suspend/resume is working.

> I cannot activate hibernation at all.
If you are using Xubuntu 12.04, then please note that hibernation is disabled by default. To re-enable it, follow these instructions: [http://askubuntu.com/questions/94754/how-to-enable-hibernation-in-12-04]("http://askubuntu.com/questions/94754/how-to-enable-hibernation-in-12-04").

---

### Post by Toz on 2012-08-08
> **Austin Texas said:**
> It is very easy to view your log files in 12.04 LTS
Open the Log File Viewer.

Austin Texas,
The Log File Viewer is not installed by default in Xubuntu. It is available for installation in the gnome-utils package, but note that it will also install other gnome packages as dependencies.

---

### Post by isosavi on 2012-08-10
> **Toz said:**
> Hello isosavi and welcome to the forums.

Can you please confirm that your problem is the same - errant messages in syslog when suspending? If so, you can safely ignore them if suspend/resume is working.

If you are using Xubuntu 12.04, then please note that hibernation is disabled by default. To re-enable it, follow these instructions: [http://askubuntu.com/questions/94754/how-to-enable-hibernation-in-12-04](http://askubuntu.com/questions/94754/how-to-enable-hibernation-in-12-04).

Yes, this is happening during suspend and resume. I can see that from syslog.

Thanks, I will try to activate hibernation!

---

### Post by thx123 on 2013-01-06
I use T500 first with xubuntu 12.04, then ubuntu 12.04, and have the exactly same error, namely:

...Device 00:0a failed to resume: error -19

It seemed to be a benign error until my T500 had been suspended for a dozen of times, when the aforementioned error accumulated enough times to cause my ubuntu to hang and force it to be shut-down to recover.

---


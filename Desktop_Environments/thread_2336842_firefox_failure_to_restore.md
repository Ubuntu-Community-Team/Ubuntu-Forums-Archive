---
title: "firefox failure to restore"
date: 2016-09-11
forum: Desktop Environments
---

### Post by Skaperen on 2016-09-11
i see this kind of thing happen with *firefox* when i shutdown the previous day with some network connected web site still connected. the TCP connection is gone.  but in this case it is a local file that still exists (restarting *firefox* loads it ok).  any idea why *firefox* is doing this?

[http://skaperen.s3-website-us-east-1.amazonaws.com/ubuntuissues/firefox-restore-fail.png](http://skaperen.s3-website-us-east-1.amazonaws.com/ubuntuissues/firefox-restore-fail.png)

sorry for the big image.  i like to make full use of the 1920x1080 display.

---

### Post by &amp;KyT$0P# on 2016-09-12
That means Firefox didn't quit properly.  Is it crashing on quit, any related reports in about:crashes?

---

### Post by Skaperen on 2016-09-12
it got a SIGTERM.  I have also tried SIGQUIT, SIGUSR1, SIGUSR2, and SIGHUP.  they all do this.  it seems the only way to make firefox quit gracefully is via its GUI interface. is that intended?  i can undestand such an intention for SIGTERM but they should have at least some signal do a graceful quit. i suggest it be SIGHUP.

---


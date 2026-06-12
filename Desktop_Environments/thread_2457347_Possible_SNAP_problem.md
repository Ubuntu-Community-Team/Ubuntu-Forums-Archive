---
title: "Possible SNAP problem"
date: 2021-01-31
forum: Desktop Environments
---

### Post by thumper76 on 2021-01-31
I am repeatedly getting this message in my SYSLOG file:

**Using '/tmp' paths in SNAP environment will lead to unreadable resources**

Will this cause a problem or should I ignore it?

(Ubuntu 20,04)

---

### Post by deadflowr on 2021-01-31
Here's a bug report with possible insight:
[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1821765]("https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1821765")
In that particular case it seems to be indicator related, not sure what snap you have that is causing the output.

---


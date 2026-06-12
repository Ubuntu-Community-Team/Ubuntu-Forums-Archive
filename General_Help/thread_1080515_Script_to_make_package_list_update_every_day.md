---
title: "Script to make package list update every day?"
date: 2009-02-25
forum: General Help
---

### Post by josephellengar on 2009-02-25
I put a script that says:
#!/bin/bash
apt-get update
in cron.daily, but it doesn't seem to be working.  What's wrong with this?  Thanks.

---

### Post by opscure on 2009-02-25
apt-get update usually requires superuser privileges.
You can try gksudo apt-get update, but this will prompt you for a password when cron runs the job.

A better way might be to use the software sources application in the system menu and under the updates tab set the option to check for updates at whatever interval you choose.  I believe this will update your repository listings for you.

---


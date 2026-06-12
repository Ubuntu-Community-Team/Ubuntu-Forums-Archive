---
title: "Oops!!! Deleted /var/log/"
date: 2005-05-26
forum: Desktop Environments
---

### Post by himuraken on 2005-05-26
I was clearing some bogus directories and files and accidentally executed: sudo rm -rf /var/log/    I recreated the directory and restarted the system. On boot I got an error stating that /var/log didn't exist but after logging in I checked and all the standard logs were in the directory. Are they any long term issues here? Or is this totally benign?

---

### Post by shakin on 2005-05-26
You should be ok. Check owner (root:root) and permissions (drwxr-xr-x) on that directory and reboot again. The error message should not appear.

---

### Post by stoneguy on 2005-05-26
What lucky star were you born under? Of all the places to do rm -rf, you picked one causing minimal damage.

Everything's got to be able to create its own log files the first time it gets run, so that's why you see everything there now. Although you've lost a bunch of install, startup, and history loginfo that might be useful for troubleshooting, you should be able to go forward okay.

---


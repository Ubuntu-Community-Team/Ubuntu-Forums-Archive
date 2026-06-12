---
title: "rsync gobbles resources 12.04"
date: 2013-10-23
forum: Desktop Environments
---

### Post by dgermann on 2013-10-23
Friends--

Rsync is gobbling resources, and I do not know why. Can you help me tame the monster?

Symptom: When rsync is running a backup, it locks up the machine, so that it takes 30-60 seconds to open a directory in LibreOffice, and another 30-60 seconds to open the file once it shows up in the list and I can click on it.

The sytem: This is a production environment. I am working on desktop box that is less than one year old, running Ubuntu 12.04 64 bit. The server is a box that is probably 5 or 6 years old, running Ubuntu 12.04 (3.2.0-54-generic-pae).

This is the root crontab command I am currently running that is giving the problems:
```
35 1,11,19 * * *	   /usr/bin/nice -n 9 rsync -a --delete ~doug/.thunderbird/7d7zoxfq.default/Mail /sam/vol22/comm/evo/tbird

```

(/sam is the mount point for the server.)

I have tried running this without the nice command and with settings such as -n 19, and I think as -n -19, and without the nice command. All with the same results.

I want to be able to have this run every hour, but I my health would not allow the high blood pressure that often while I am waiting! <grin>

I did not have this problem when I was running this command under 10.04 (but it was on an older machine).

Thanks!

---


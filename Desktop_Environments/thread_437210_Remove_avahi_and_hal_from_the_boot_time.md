---
title: "Remove avahi and hal from the boot time"
date: 2007-05-08
forum: Desktop Environments
---

### Post by lucho115 on 2007-05-08
I have used sysvconfig, rcconf, sysv-rc-conf but i cant remove avahi and hal from the boot time, i dont know where to look the find in what place they are loaded? anybdy can helpme?
thks

---

### Post by lucho115 on 2007-05-08
i know that ubuntu uses upstart instead of system v but i cannt find info or docs about.
thks

---

### Post by lucho115 on 2007-05-09
I use this file yet, i config like this:

```
AVAHI_DAEMON_START=0
```

but it still start at boot time.

With hal i use in /etc/default/hal this code 
```
 DAEMON_OPTS=NO
```

but it still start at boot time.

---

### Post by afzalnaj on 2007-08-11
try these

[https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/65587](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/65587)
[https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/65587/comments/6](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/65587/comments/6)

im a complete newbie, i dont even know what avahi is and what they are talking about but i guessed from the talk that this might work

---


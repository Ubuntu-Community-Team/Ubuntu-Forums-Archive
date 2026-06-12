---
title: "ntp update on boot"
date: 2006-01-25
forum: Desktop Environments
---

### Post by alamba on 2006-01-25
Hi,

How can I turn off the ntp update on boot? Tried chkconfig --list but that doesn't seem to work in ubuntu.

Akshay

---

### Post by d1337 on 2006-01-25
A shortcut to skip some of the boot steps is to hit ctrl-c when it hangs on them...but that may get old (I do it on my laptop without even thinking about it).  Otherwise, there is a project called BUM (Boot Up Manager) that may be of some help.  It's in the forums under Other Ubuntu Support - 3rd Party Ubuntu Projects...here is a [link]("http://ubuntuforums.org/forumdisplay.php?f=75").  There is likely another way, but that's what came to mind.

d1337

---

### Post by alamba on 2006-01-25
Thanks for the link. Guess BUM is the way to go. Wonder why they don't have chkconfig in the distribution though. The ctrl-c thing works when you're around, I typically switch on my laptop & my desktop and go grab a smoke while it's booting.

Akshay

---

### Post by bulldogzerofive on 2006-01-25
Go to /etc/init.d and comment out ntpdate.

---

### Post by alamba on 2006-01-25
which file in /etc/init.d?

---

### Post by scubajeff on 2006-01-25
I think the ntp sync is not a bad thing, what bother me (and maybe most of us) is that it will sync on every boot. So here is my solution to this issue, I modified the file /etc/init.d/ntpdate so that it only sync with ntp server on Friday. Here's the new code:
```

#!/bin/sh

PATH=/sbin:/bin

[B]DATE=`date +%u`
if [ $DATE -eq 5 ]; then
[/B]
...
**fi**

```

---

### Post by alamba on 2006-01-25
Cool...that's a much better solution! Thanks. Will implement it right away.

Akshay

---

### Post by dcstar on 2006-01-25
[QUOTE=bulldogzerofive]Go to /etc/init.d and comment out ntpdate.[/QUOTE]

Edit /etc/default/ntpdate and comment out all the servers, that way you aren't mucking up the startup scripts and you can choose to add in other servers later.

---

### Post by alamba on 2006-01-25
Thanks david. U're right i'll rather not muck up the startup scripts.

Akshay

---


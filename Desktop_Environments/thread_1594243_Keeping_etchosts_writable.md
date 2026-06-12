---
title: "Keeping /etc/hosts writable"
date: 2010-10-12
forum: Desktop Environments
---

### Post by scribu on 2010-10-12
So, updated to Ubuntu 10.10 Sunday and it's great :) except for this one little thing that is really bugging me.

I use SwitchHosts, a plugin for Firefox which requires that /etc/hosts be writable. I make it writable, but when I restart, it's back to it's non-writable state.

I did not have this problem until upgrading to Maverick.

Any ideas what might be causing this?

I've tried adding the *chmod 666 /etc/hosts* command in various places, to be executed at startup, but it doesn't seem to work.

---

### Post by James78 on 2010-10-12
You could chown it to your user and group, then add the suid and guid bit to it, and see if that does the trick for you.

```
toonarmy@opti-hacker:/etc$ ls -l hosts
-rw-r--r-- 1 root root 382 2010-10-11 07:47 hosts
toonarmy@opti-hacker:/etc$ sudo chown toonarmy. hosts
toonarmy@opti-hacker:/etc$ sudo chmod ug+s hosts
toonarmy@opti-hacker:/etc$ ls -l hosts
-rwSr-Sr-- 1 toonarmy toonarmy 382 2010-10-11 07:47 hosts
```

---

### Post by scribu on 2010-10-12
Thanks for answering.

I tried that, but it got reset after I restarted.

---

### Post by I_can_see_the_light on 2010-10-12
Perhaps it's possible to edit */etc/rc.local* and add the command needed (without sudo)? 

Don't forget to make it executable afterwards though.

---

### Post by scribu on 2010-10-13
That seems to do the trick. Thanks!

---


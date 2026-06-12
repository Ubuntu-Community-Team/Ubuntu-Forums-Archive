---
title: "gnome-do crashing with most recent upgrade"
date: 2008-07-28
forum: Desktop Environments
---

### Post by igray78756 on 2008-07-28
I just got a new update to gnome-do today (hardy-heron and [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) hardy main) and as soon as I started it, it began crashing about 1 minute after starting.

If you experience the same problem, I fixed it with the following command:

```
sudo ln -s /usr/lib/notification-daemon/notification-daemon /usr/local/libexec/
```

Apparently, gnome-do was looking for the notification-daemon in the wrong place when it wanted to nofify me of new updates to my plugins.

Hope this helps somebody else...

---

### Post by tamoneya on 2008-07-28
Looks good to me.  Have you notified the developers or filed a bug report?

---

### Post by quickfished on 2008-07-29
I had the same problem.  Disabling the Evolution plugin stopped Do from crashing, so logically it has something to do with that.

---

### Post by donkeyX on 2009-03-05
I have this same problem with 32b version of intrepid but by adding the ln seemed to break the notification all together. I have just disabled all but one of the plugins and will activate slowly to see which one is the broken one. 

PS: i did not have evolution enabled :( so it is not that one.

---


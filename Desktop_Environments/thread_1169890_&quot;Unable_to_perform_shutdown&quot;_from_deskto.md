---
title: "&quot;Unable to perform shutdown&quot; from desktop"
date: 2009-05-25
forum: Desktop Environments
---

### Post by abovett on 2009-05-25
I am running Xubuntu 9.04. If I try to shut down from the desktop I get a dialogue with the following message:

```
Unable to perform shutdown
org.freedesktop.hal.power-management.shutdown no
<--(action, result)

```

This dialogue offers one button - "Quit". Clicking it takes me back to the logon screen. Shut Down from there works fine.

Anyone got any ideas?

Thanks

Andy

---

### Post by tors on 2009-06-05
I experience a similar thing in Xubuntu Jaunty, using Action Button "Quit" from menubar and then choosing "Restart":

Unable to perform shutdown
org.freedesktop.hal.power-management.reboot-multiple-sessions auth_admin <-- (action, result)

After confirming this error message I end up at the login screen, from where I am able to restart.

---

### Post by kerry_s on 2009-06-05
> **tors said:**
> I experience a similar thing in Xubuntu Jaunty, using Action Button "Quit" from menubar and then choosing "Restart":

Unable to perform shutdown
org.freedesktop.hal.power-management.reboot-multiple-sessions auth_admin <-- (action, result)

After confirming this error message I end up at the login screen, from where I am able to restart.

make sure your in the admin group:

press** alt+f2**
type> **gksudo mousepad /etc/group**

---

### Post by centyx on 2009-06-30
I am experiencing this issue also. My user already belongs to the admin group.

Any ideas/suggestions?

Thanks!

---

### Post by kerry_s on 2009-06-30
> **centyx said:**
> I am experiencing this issue also. My user already belongs to the admin group.

Any ideas/suggestions?

Thanks!

and your error says what?

---

### Post by centyx on 2009-06-30
Thanks for the quick reply.

Error is same as the two above, but I've found that it is due to this bug:

[https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/251337](https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/251337)

I've implemented ( though undesirable ) workaround suggested here:

[https://lists.ubuntu.com/archives/xubuntu-users/2009-June/001783.html](https://lists.ubuntu.com/archives/xubuntu-users/2009-June/001783.html)

Thanks!

---


---
title: "Blank White Screen at login (LightDM Greeter)"
date: 2015-07-03
forum: Desktop Environments
---

### Post by jmarriott76 on 2015-07-03
Hi,

I have the same issue as [http://ubuntuforums.org/showthread.php?t=2267474](http://ubuntuforums.org/showthread.php?t=2267474) - I am seeing a blank white screen instead of the login screen. Clicking anywhere on the screen then shows the login. Also, I am seeing this on both monitors as well as the login appearing on both monitors.

No, I do not have mirror mode enabled. I have set up two users and the issue is with both (also same when there was only one user).

In the previous posters thread they were able to fix the issue by updating LightDM Greeter. The links posted are no longer available.

Please advise if the solution would be the same and if so, how I would update LightDM Greeter.

Many thanks in advance.

Xubuntu 15.04, dual monitors.

```
ls -la /etc/lightdm total 24
drwxr-xr-x   2 root root  4096 Jul  2 16:42 .
drwxr-xr-x 133 root root 12288 Jul  3 11:08 ..
lrwxrwxrwx   1 root root    55 Jul  2 16:28 lightdm-gtk-greeter.conf -> /etc/alternatives/lightdm-gtk-greeter-config-derivative
-rw-r--r--   1 root root  2765 Feb 15 20:01 lightdm-gtk-greeter-ubuntu.conf
-rw-r--r--   1 root root   452 Apr  8 10:29 users.conf
```

Attached is the log from /var/logs/lightdm/

---

### Post by ihoe3fze on 2015-07-06
Version 2.0.1 already contains fix for this bug (it's the reason why links are no available). You can use this PPA to get updated version for 15.04:
[https://launchpad.net/~lightdm-gtk-greeter-team/+archive/ubuntu/stable](https://launchpad.net/~lightdm-gtk-greeter-team/+archive/ubuntu/stable)

---


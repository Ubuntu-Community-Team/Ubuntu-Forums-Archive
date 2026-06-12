---
title: "update-notifier won't run"
date: 2009-03-14
forum: General Help
---

### Post by ubernoob on 2009-03-14
Hi! 

I can't get update-notifier to run. Is the problem my low uid?

```

myuser@ubuntu:~$ update-notifier 

** (update-notifier:25915): WARNING **: not starting for system user

myuser@ubuntu:~$ cat /etc/passwd | grep myuser
myuser:x:164:164:MyUser,,,:/home/myuser:/bin/bash

myuser@ubuntu:~$ cat /etc/group | grep myuser
adm:x:4:myuser
dialout:x:20:myuser
cdrom:x:24:myuser
plugdev:x:46:myuser
lpadmin:x:110:myuser
admin:x:119:myuser
myuser:x:164:
sambashare:x:124:myuser
```

---

### Post by geirha on 2009-03-14
Seems like it. From the source code of the version in intrepid: [http://update-notifier.sourcearchive.com/documentation/0.71.8/update-notifier_8c-source.html](http://update-notifier.sourcearchive.com/documentation/0.71.8/update-notifier_8c-source.html)
```

00357 gboolean
00358 system_user()
00359 {
00360    /* do not start for system users, e.g. the guest session 
00361     * (see /usr/share/gdm/guest-session/guest-session-setup.sh)
00362     */
00363    uid_t uid = getuid();
00364    if (uid < 500)
00365       return TRUE;
00366    return FALSE;
00367 }

```

---

### Post by ubernoob on 2009-03-14
Argh! :( I can't change my uid since it's used on several systems which i don't control.

It is already fixed in next version of ubuntu:
[https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/294569](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/294569)

Downloading it manually will probably breake my system cause of dependencies:
[http://packages.ubuntu.com/jaunty/update-notifier](http://packages.ubuntu.com/jaunty/update-notifier)

Is there a way to get it fixed in 8.10?

---

### Post by KCG102282 on 2009-03-14
> **ubernoob said:**
> Argh! :( I can't change my uid since it's used on several systems which i don't control.

It is already fixed in next version of ubuntu:
[https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/294569](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/294569)

Downloading it manually will probably breake my system cause of dependencies:
[http://packages.ubuntu.com/jaunty/update-notifier](http://packages.ubuntu.com/jaunty/update-notifier)

Is there a way to get it fixed in 8.10?
I doubt it. I would check the dependencies to make sure it won't break and then if it wont install it or just use apt-get upgrade.

---


---
title: "Installed Gnome 3 from the Ubuntu Software Center.  Now I cannot boot Ubuntu 12.04"
date: 2012-09-27
forum: Desktop Environments
---

### Post by dspi on 2012-09-27
Hello,
I Installed Gnome 3 from the Ubuntu Software Center.  Now I cannot boot Ubuntu 12.04.

Afterwards I read that the Ubuntu Software Center is not the best place to install from...but it's too late now.

When I turn on the computer, I get a new Grub background (with a Debian space scene).  After selecting Ubuntu, I get messages such as
```

Stopping save kernel messages
Starting CUPS printing spooler/server
Stopping System V runlevel compatibility

```Is there any way I can fix this?

(There must be quite a few people who've encountered this, but I can't seem to find any posts with solutions.)

---

### Post by dspi on 2012-09-27
**More info:**

Booting into a recovery mode, I'm offered the option to "Drop to root shell prompt".

From there, I tried > apt-get install gnome-shell, but get the following message:

```

W:  Not using locking for read only file /var/lib/dpkg/lock
E:  dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct
the problem.

```Ttying that, and I get:
```

dpkg:  error:  unable to access dpkg status area:  Read-only file system

```

---

### Post by black veils on 2012-09-27
i'm not sure about what your problem is, but about recovery mode, you need to gain read-write privileges first, and enable internet access. this can be done by choosing the network option in recovery mode first, then dropping to root shell.

---


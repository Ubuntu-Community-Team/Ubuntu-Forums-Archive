---
title: "umask on Ubuntu 12.04.1 LTS"
date: 2013-02-13
forum: Desktop Environments
---

### Post by UXMan on 2013-02-13
I've being trying to set the umask on my Ubuntu 12.04.1 LTS installation to 077 and haven't been able. I've edited the /etc/login.defs to set the umask to 077 and also edited the following files:

/etc/init.d/bootlogd:   umask 077
/etc/init.d/rc:             umask 077
/etc/init.d/ssh:           umask 077
/etc/init.d/umountfs:   umask 077
/etc/init.d/urandom:    umask 077
/etc/init.d/urandom:    umask 077
/etc/init.d/urandom:    umask 077

None of these changes impacted the directory and file creation. Everytime I create a new directory/file I get a result of 022 umask. I must clarify that this behavior does not apply to root user. 
Could you please help me out on this one?

---

### Post by ali abry on 2013-02-13
if you want to make the change fore ever put it in ~/.bashrc  which is in your home directory.
```
 umask 0077
```

---

### Post by UXMan on 2013-02-13
What if it's not there? Where is this configuration being read from?

---

### Post by schragge on 2013-02-13
On a Debian-based system, it's usually from */etc/login.defs*, but can be set e.g. in */etc/profile*, too. But setting it in your *~/.bashrc* overrides the system-wide default.

---

### Post by UXMan on 2013-02-13
Alright guys, i figured it out.

/etc/bash.bashrc is the system-wide bash profile config. You can set the umask you need on this file and will be system-wide, as previously said. *~/.bashrc* will override the system-wide /etc/bash.bashrc.

You can mark this thread as being solved.

Thanks to everyone!

---


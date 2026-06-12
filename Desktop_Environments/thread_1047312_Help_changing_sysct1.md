---
title: "Help changing sysct1"
date: 2009-01-22
forum: Desktop Environments
---

### Post by chapalabill on 2009-01-22
I am running ubuntu 8.10 and need to make some changes to my usr/sysct1 to solve some banking log on issues.  I try following the directions but am not allowed to make the change and save.  What am I doing wrong?

---

### Post by XanTrax on 2009-01-22
> **chapalabill said:**
> I am running ubuntu 8.10 and need to make some changes to my usr/sysct1 to solve some banking log on issues.  I try following the directions but am not allowed to make the change and save.  What am I doing wrong?

I dont quite get what you're getting at?   Do you mean you are trying to edit /etc/sysctl.d or /etc/sysctl.conf?

If you are trying to edit /etc/sysctl.conf, then run it like this:

```

sudo gedit /etc/sysctl.conf

```

or

```

sudo su -
gedit /etc/sysctl.conf

```


/etc/sysctl.d is a directory that is read by sysctl almost exactly how the settings from /etc/sysctl.conf are read/loaded by sysctl.

Possibly, reword your question?

---


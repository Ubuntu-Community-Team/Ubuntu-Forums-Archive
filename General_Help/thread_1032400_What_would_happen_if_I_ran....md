---
title: "What would happen if I ran..."
date: 2009-01-06
forum: General Help
---

### Post by xluryan on 2009-01-06
I am trying to secure my box as much as possible. What would be the consequences of me running the following commands:

```

$ cd /
$ sudo chmod -R o-rwx *

```

Basically disallowing read/write/execute permissions for *others* on all directories and their sub-directories.

---

### Post by blazemore on 2009-01-06
Don't cron jobs run under their own user alias?

---

### Post by bodhi.zazen on 2009-01-06
You would break Ubuntu. Users need to be able to read system files and run applications (users do not (should not) own anything outside of their home directory).

---

### Post by sisco311 on 2009-01-06
> **xluryan said:**
> I am trying to secure my box as much as possible. What would be the consequences of me running the following commands:

```

$ cd /
$ sudo chmod -R o-rwx *

```

Basically disallowing read/write/execute permissions for *others* on all directories and their sub-directories.

you would break your system.

the directories in the root ("/") are owned by root:root

if you remove the x permission, then only the applications started with root privileges will be allowed to read the files in /etc /usr /lib ... directories.

---


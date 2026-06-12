---
title: "Apt-get install/upgrade errors"
date: 2006-08-07
forum: Desktop Environments
---

### Post by detour on 2006-08-07
Trying to upgrade gives me the following error:
```

(Reading database ... dpkg: error processing /var/cache/apt/archives/gnupg_1.4.2.2-1ubuntu2.2_i386.deb (--unpack):
 unable to open files list file for package `cedega-small': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/gnupg_1.4.2.2-1ubuntu2.2_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Trying to remove the cedega package gives this error:
```

(Reading database ... dpkg: error processing cedega-small (--remove):
 unable to open files list file for package `cedega-small': Input/output error
Errors were encountered while processing:
 cedega-small
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Anyone know how I can fix this? I am afraid of messing around with the gnupg package because I am fairly certain that it is used internally to verify signatures and whatnot. I have tried 'apt-get clean' as well as 'Synaptic -> Fix broken packages'. As it stands I cannot install or upgrade anything. Thanks.

---


---
title: "Users and groups, groups settings,group properties, group members area only 1 line"
date: 2019-11-23
forum: Desktop Environments
---

### Post by hvieren on 2019-11-23
lubuntu 18.04
/usr/bin/perl /usr/share/system-tools-backends-2.0/scripts/SystemToolsBackends.pl -m GroupsConfig
the display area for the members is only 1 line high

panel starts out with 2 visible lines but when moving cursor into panel , it shrinks to 1 line.

---

### Post by SeijiSensei on 2019-11-23
Have you tried managing users and groups from the command prompt?

```

sudo adduser -p PaSSworD -G biggroup bill

```

will create a user named "bill" with group "bill" (the default) and also add that user to the biggroup group.

[https://manpages.ubuntu.com/manpages/bionic/man8/adduser.8.html](https://manpages.ubuntu.com/manpages/bionic/man8/adduser.8.html)

---


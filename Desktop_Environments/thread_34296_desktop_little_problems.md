---
title: "desktop little problems"
date: 2005-05-14
forum: Desktop Environments
---

### Post by spolu on 2005-05-14
Hello, I'm a new user of ubuntu distro and I'm very satisfied by this wonderful distribution !

Nevertheless i still have one minor problem :

When i launch an administration UI that needs root password, a windows appear asking me to give this pass (everything normal) but when i give it, the program simply dead with different type of error and there's an error windows that appears :

failed to run /usr/bin/synaptic (as an example)
child terminated with 1 status.


Maybe i misconfigured something...

Could you help please even if it is not very disturbing since i can run the program from a root console...

Thanks very much

Best regards

Stanislas POLU

---

### Post by Xian on 2005-05-14
[QUOTE=spolu]failed to run /usr/bin/synaptic (as an example)
child terminated with 1 status.


Maybe i misconfigured something...
[/QUOTE]
It sounds as if you are for some reason not a member of the sudoers group.
Read this page at the wiki: [RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)

---


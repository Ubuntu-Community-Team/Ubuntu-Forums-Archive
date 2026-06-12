---
title: "&quot;Could not initialize the package information&quot; error??????"
date: 2009-04-17
forum: General Help
---

### Post by wolfman1221 on 2009-04-17
I received this error while trying to update my system. 


"
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Could not open file /var/lib/dpkg/status - open (2 No such file or directory), E:The package lists or status file could not be parsed or opened.'

"

If anyone could help me with this, I would truly appreciate it.

---

### Post by meeko on 2009-04-17
First check to see if you see a file named "status"

```
ls -la /var/lib/dpkg/
```

If you do not have a file named status and you do have a file named "status-old", then rename that file to "status" and you should be fine.

```
sudo mv /var/lib/dpkg/status-old /var/lib/dpkg/status
```

This *should* fix your problem. Please advise.

---

### Post by wolfman1221 on 2009-04-17
That is what came back


"mv: cannot stat `/var/lib/dpkg/status-old': No such file or directory"

---


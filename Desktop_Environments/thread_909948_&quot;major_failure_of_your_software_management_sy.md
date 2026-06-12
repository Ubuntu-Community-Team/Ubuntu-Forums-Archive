---
title: "&quot;major failure of your software management system&quot;"
date: 2008-09-04
forum: Desktop Environments
---

### Post by webcrawler559 on 2008-09-04
This message appears when I try to open Add/Remove Applications:

```
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
```

This, when I try to open Update Manager:
```

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Could not open file /var/lib/dpkg/status - open (2 No such file or directory), E:The package lists or status file could not be parsed or opened.'
```

And this when I try to open Synaptic Package Manager:
```

E: Could not open file /var/lib/dpkg/status - open (2 No such file or directory)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
```

I've tried everything suggested in each of the error codes...and Report a Problem won't open...

...suggestions?

---

### Post by vikasmk on 2008-09-04
this happpened when i forcibly installed outdated librairies using dpkg
 
 give us the result of 
 dpkg -a --configure

---


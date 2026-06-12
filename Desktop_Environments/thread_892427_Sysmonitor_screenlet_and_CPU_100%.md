---
title: "Sysmonitor screenlet and CPU 100%"
date: 2008-08-17
forum: Desktop Environments
---

### Post by alphe323 on 2008-08-17
Every time I login the CPU goes to 100%.

The processes that do this are:
 sh -c { lsb release -is; } > 2>&1
 sh -c { apt-cache policy 2>/dev/null; } 2>&1

Both of them are invoked from screenlet Sysmonitor.

It remains to 100% until I execute manual "sudo apt-get update" and then goes back to normal levels.

---


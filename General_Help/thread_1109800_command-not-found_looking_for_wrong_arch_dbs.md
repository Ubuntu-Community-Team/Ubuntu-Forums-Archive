---
title: "command-not-found looking for wrong arch dbs"
date: 2009-03-29
forum: General Help
---

### Post by wdaniels on 2009-03-29
I'm seeing an error from command-not-found:

```
Unable to open binary database /usr/share/command-not-found/programs.d/i386-universe.db: (22, 'Invalid argument')
Unable to open binary database /usr/share/command-not-found/programs.d/i386-restricted.db: (22, 'Invalid argument')
Unable to open binary database /usr/share/command-not-found/programs.d/i386-main.db: (22, 'Invalid argument')
Unable to open binary database /usr/share/command-not-found/programs.d/i386-multiverse.db: (22, 'Invalid argument')
bash: foo: command not found
```

I checked my command-not-found-data package and, as expected and as is correct, the architecture prefix for the db files is amd64 not i386. So can anybody tell me where the config file is that points command-not-found at the databases so I can fix this? I tried just purging and re-installing command-not-found[-data] packages but this does not help.

I should note that I'm running the Jaunty Beta right now, but I'm fairly sure this was happening before I upgraded.

---


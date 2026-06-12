---
title: "Way to configure Compiz from command line?"
date: 2011-10-20
forum: Desktop Environments
---

### Post by ucoder on 2011-10-20
Hi!

Is there a way to import settings for Compiz from a script? For my surprise I haven't found an easy way to do this as all documentation refers to using CCSM, but I'd need to automate configuring the settings from a script.

Thanks!

---

### Post by stinkeye on 2011-10-20
> **ucoder said:**
> Hi!

Is there a way to import settings for Compiz from a script? For my surprise I haven't found an easy way to do this as all documentation refers to using CCSM, but I'd need to automate configuring the settings from a script.

Thanks!

Can you not use ccsm preferences to export your current profile and then import
when setting a new profile.

---

### Post by ucoder on 2011-10-20
Yes, but I want to do that from a script, without the GUI.

---

### Post by stinkeye on 2011-10-20
If it's any help you'll find your compiz plugin settings in
```
~/.gconf/apps/compiz-1/plugins
```

---


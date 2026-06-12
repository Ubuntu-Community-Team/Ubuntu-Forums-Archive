---
title: "No current session tab"
date: 2009-02-03
forum: General Help
---

### Post by OliverN on 2009-02-03
I want to change the startup order of a certain application, but I don't have a "current session" tab in gnome-session-properties. Is this a bug and how do I change my startup order then?

---

### Post by rozbarwinek on 2009-02-03
> **OliverN said:**
> I want to change the startup order of a certain application, but I don't have a "current session" tab in gnome-session-properties. Is this a bug and how do I change my startup order then?

You can change it by creating a bash script, make it executable and add it to sessions.

For example:

```
#!/bin/bash
sleep 20 && conky &
sleep 30 && mail-notification &
```

Of course if you don't want them to load after some time delete "sleep" option.

---


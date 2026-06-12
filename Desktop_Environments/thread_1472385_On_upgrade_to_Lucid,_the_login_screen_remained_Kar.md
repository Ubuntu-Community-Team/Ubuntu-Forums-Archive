---
title: "On upgrade to Lucid, the login screen remained Karmic's one."
date: 2010-05-04
forum: Desktop Environments
---

### Post by leandromartinez98 on 2010-05-04
That's it. The upgrade was essentially flaweless, but the login screen
remained the brown one from karmic. I don't know how to solve that
any ideas? There is no option anymore on system->login screen to 
change that.

---

### Post by _0R10N on 2010-05-04
You can configure that running
```
gksudo -u gdm dbus-launch gnome-appearance-properties
```

Kind regards!

---

### Post by leandromartinez98 on 2010-05-05
> **_0R10N said:**
> You can configure that running
```
gksudo -u gdm dbus-launch gnome-appearance-properties
```

Kind regards!

Thanks! So that corresponds to changing the root theme. I would
never figure it out.

---

### Post by _0R10N on 2010-05-05
> **leandromartinez98 said:**
> Thanks! So that corresponds to changing the root theme. I would
never figure it out.
You're welcome!!

Yeah, is the root theme (main theme) not root user theme...

If you look carefully, you'll see ```
 -u gdm
``` that means that the changes are performed for the gdm user.

---


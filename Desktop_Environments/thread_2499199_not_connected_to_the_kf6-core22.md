---
title: "not connected to the kf6-core22"
date: 2024-07-18
forum: Desktop Environments
---

### Post by dakspyker on 2024-07-18
So digikam snap seems to have decided to upgrade itself without any warning to the user, and now suddenly it will not launch, with:

```

[FONT=monospace][COLOR=#54ff54]**johann@sny**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ digikam  [/COLOR]
ERROR: not connected to the kf6-core22 content interface.
[/FONT]
```

How do I fix this?

Thanks!
J

---

### Post by #&amp;thj^% on 2024-07-18
Got to love those snaps, have you tried to manually connecting it?
```
snap connect digikam:kf6-core22 kf6-core22:kf6-core22-slot
```

However this should be fixed: [https://forum.snapcraft.io/t/kde-global-auto-connect-request/39535/2](https://forum.snapcraft.io/t/kde-global-auto-connect-request/39535/2)

---

### Post by dakspyker on 2024-07-21
Thank you! It is working now.

---


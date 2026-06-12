---
title: "gui run commands"
date: 2005-10-16
forum: Desktop Environments
---

### Post by OldGaf on 2005-10-16
Hi,

I know I can start the KDE Control Center by clicking “Run Command” and typing “kcontrol”.
Is there a list of other “Run” commands to start other things like “Remote Places” ?

I need this info for creating Karamba scripts and because I have problems accessing the Admin rights from in some of my apps. so I need to run “sudo kcontrol” etc.

---

### Post by GeneralZod on 2005-10-17
Hi there,

I'm not quite sure what you mean, but you can actually run any apps from the "Run Command" dialog; e.g.

```

konqueror remote:/

```

Let us know some examples of what you want to do, and we'll see if we can help :)

```

kdesu konqueror

```

will prompt for your password before launching konqueror as root.

---

### Post by OldGaf on 2005-10-18
```

konqueror remote:/

```

Ah..... I think that was the bit I was missing.....

I was trying to use
```

remote:/

```
(in a karamba script) and nothing was happening. I will add konqueror to it when I get home from work tonight.

Thanks for responing!

---


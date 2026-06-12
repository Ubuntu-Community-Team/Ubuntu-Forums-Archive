---
title: "making sure the daemon message bus is running"
date: 2009-03-28
forum: General Help
---

### Post by imparja2 on 2009-03-28
When there are too many things open my computer crashes and reports that I should check that the message bus daemon is running so how do I do that and how do I get it running again?

---

### Post by 3rdalbum on 2009-03-28
That's rather strange that Dbus is crashing, but you should be able to start it again with this command:

```
/bin/dbus-daemon --system
```

That might need to be run with sudo - I don't know as I've never had Dbus crash.

---

### Post by imparja2 on 2009-03-28
so how do I run with sudo
what should I type in the command line?
I'm not just an ubuntu beginner I don't know much about computers

---


---
title: "Help, can't copy files to usr/share"
date: 2009-03-08
forum: General Help
---

### Post by runebinder on 2009-03-08
Trying to add some widgets to screenlets, found the folder for screenlets which is in usr/share, yet when I try to copy into that folder I get the message:

"You don't have the right permissions to extract archives in the folder "file:///usr/share/screenlets"

I've looked under Users and Groups and Authorisations yet can't see any options that would apply. Anyone got any ideas for what I need to do to fix this?

Ian.

---

### Post by taurus on 2009-03-08
```
**sudo** cp filename /usr/share/screenlets
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by runebinder on 2009-03-09
Thanks Taurus, will have a read and give it a try.

---


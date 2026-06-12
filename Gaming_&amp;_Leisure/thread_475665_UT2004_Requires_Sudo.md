---
title: "UT2004 Requires Sudo"
date: 2007-06-16
forum: Gaming &amp; Leisure
---

### Post by phr0ze on 2007-06-16
I can only run UT with sudo. If I run it without it fails because of some permissions. UT ended up installing into /usr/local/games/ut2004 which is the default location. Can I set some sort of permissions on this folder so I don't have to use sudo.

Thanks,
John

---

### Post by shad0w_walker on 2007-06-16
I assume you installed using sudo?

When you installed did you press the play now button when the installer was finished? If you did thats probably the cause of your problems. Try running this command and see if it helps:

```
sudo chown -R $USER ~/.ut2004
```

---


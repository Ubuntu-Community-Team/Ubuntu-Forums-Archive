---
title: "New shortcut on desktop as root to open software"
date: 2006-09-13
forum: Desktop Environments
---

### Post by ofer_w on 2006-09-13
I have software that should load as root and when doing shortcut on desktop it is open as the user rights and not as root

How it is possible to give the command that the software will open as root?

The software is under /usr/local/...

Thanks

---

### Post by nereid on 2006-09-13
Prepend the application in your link with gksudo.

```

gksudo /usr/local/bin/app_for_root

```

---

### Post by ayoli on 2006-09-13
morever, if your app takes arguments, you need to quote like this example:
```
gksudo "/usr/bin/nautilus --no-desktop"
```
note that full path is not required if the binary stands in a path registered in $PATH environement var (ie: /usr/bin, /usr/local/bin)

---

### Post by ofer_w on 2006-09-13
> **nereid said:**
> Prepend the application in your link with gksudo.

```

gksudo /usr/local/bin/app_for_root

```

Thanks working good :-)

---


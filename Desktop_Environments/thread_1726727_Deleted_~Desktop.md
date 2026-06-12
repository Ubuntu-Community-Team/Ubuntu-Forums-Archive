---
title: "Deleted ~/Desktop"
date: 2011-04-11
forum: Desktop Environments
---

### Post by pgpoulsen on 2011-04-11
Hi

I accidently deleted my ~/Desktop so now all the content of my ~/ folder is shown on the desktop. I have tried to create a ~/Desktop directory but it doesn't help. The /app/nautilus/preferences/desktop_is_home_dir is set to false.

Anyone?

/peter

---

### Post by wojox on 2011-04-11
Go into your home directory and Ctrl+H to show hidden files.

Look at .config/user-dirs.dirs and see if this line is there:

```
XDG_DESKTOP_DIR="$HOME/Desktop"
```

If not add it, log out and back in.

---

### Post by pgpoulsen on 2011-04-12
Thanks. That fixed it :)

---


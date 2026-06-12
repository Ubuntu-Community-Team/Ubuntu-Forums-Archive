---
title: "Desktop Directory in Home Folder"
date: 2010-05-21
forum: Desktop Environments
---

### Post by volvolinux on 2010-05-21
Hey, I want to ask a question that the "Desktop" directory located in the "Home Folder" contain the Desktop content.
 
If I deleted this "Desktop" directory, the system will try to use "Home Folder" as the Desktop.
 
When I create the "Desktop" back, system still use the "Home Folder" as the Desktop.
 
So how can I let the system use the "Desktop" directory as the realy Desktop then?

---

### Post by wojox on 2010-05-22
Show hidden files in your home directory (Ctrl+H)

Look for /.config/user-dirs.dirs

And set this value:

```
XDG_DESKTOP_DIR="$HOME/Desktop"
```

---

### Post by volvolinux on 2010-05-22
thanks!

---

### Post by wojox on 2010-05-22
Your welcome. :)

---


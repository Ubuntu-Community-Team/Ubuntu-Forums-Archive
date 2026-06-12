---
title: "Folder permissions"
date: 2008-07-25
forum: Desktop Environments
---

### Post by notlim_hardy on 2008-07-25
I'm trying to copy an amsn plugin to /usr/share/amsn but can only do that as root. Can someone please post the exact command line i should enter so I can be able to copy that via Gnome? Thanks a lot.

---

### Post by StOoZ on 2008-07-25
precede your command with 'sudo'

---

### Post by ibutho on 2008-07-25
Run ALT-F2 and enter the command "gksudo nautilus". That will start the file manager with root privileges. If using a terminal, just prefix the copy commands with sudo.

---

### Post by GreenN00b on 2008-07-25
Press Alt+F2 to open run application window.
Enter the following command:
```
gksudo nautilus
```

This should open nautilus with root privileges.

---


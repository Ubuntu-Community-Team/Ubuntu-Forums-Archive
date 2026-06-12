---
title: "uninstalling themes"
date: 2009-02-23
forum: Desktop Environments
---

### Post by xbanex on 2009-02-23
Hello everyone i hate making a thread about this but i cant figure out how to uninstall a theme instaled by draging the files to the home directory

---

### Post by UbuntuNerd on 2009-02-23
have you try going to /usr/share/themes, if its there you need to have permission to deleted it in a terminal type this to open "nautilus" as root then browse to the location
```
gksudo nautilus
```

---

### Post by xbanex on 2009-02-23
> **UbuntuNerd said:**
> have you try going to /usr/share/themes, if its there you need to have permission to deleted it in a terminal type this to open "nautilus" as root then browse to the location
```
gksudo nautilus
```

when i try this i get an error saying
* (nautilus:6339): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


im not sure what it means

---

### Post by xbanex on 2009-02-23
ok i found the files for the them but when i delete them and restart the theme is still there

---

### Post by UbuntuNerd on 2009-02-23
did the theme you're trying to delete come with icons?

---

### Post by UbuntuNerd on 2009-02-23
also try changing the theme to something different maybe that helps.

---


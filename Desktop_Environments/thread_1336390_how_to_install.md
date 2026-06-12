---
title: "how to install?"
date: 2009-11-24
forum: Desktop Environments
---

### Post by expxe on 2009-11-24
i dl'ed a program it says

3. Installation instructions

    To configure, build and install Mail Notification, use the
    following commands:

        ./jb configure
        ./jb build
        sudo ./jb install

    Note that a number of settings can be passed to the configure
    stage, for instance:

        ./jb configure prefix=/opt cflags=-O3 pop3=no

    For details, use:

        ./jb help

    For more informations about JB (the Jean-Yves Lefort's Build
    System), read jbsrc/lib/README.

    Note to Sylpheed users: if you want more responsive
    notifications, apply the patch data/sylpheed-locking.diff to
    Sylpheed and recompile it.

soooooo, how to install? i opened up terminal and typing the text in ./jb configure doesn't work, comes back with no such file or directory .... and why not a point and click install process? it is way easier

---

### Post by snowpine on 2009-11-24
mail-notification is in the Ubuntu repositories.

```
sudo apt-get install mail-notification
```

should do the trick.

Downloading random installers from the Internet is kind of a "Windows way" of doing things. I highly recommend using the Ubuntu repositories whenever possible... that's what they're there for!

Good luck.

---


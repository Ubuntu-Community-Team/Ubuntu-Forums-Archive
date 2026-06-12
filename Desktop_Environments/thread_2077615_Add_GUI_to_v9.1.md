---
title: "Add GUI to v9.1 ?"
date: 2012-10-29
forum: Desktop Environments
---

### Post by Greg Roberts on 2012-10-29
Hi
 
I inherited a v9.1 Ubuntu vm which is used to run bugzilla. This is a command line only OS. While trying to solve another program i ran up ubuntu-9.10-desktop-amd64.iso 
 
I guess this means the "server" edition was installed ?
 
=> Is it possible to add the GUI to en existing installation, or this requires a fresh install of the OS ?
 
Thanks

---

### Post by lisati on 2012-10-29
It is possible to add a GUI to a CLI-only installation, with something like this:
```
sudo apt-get install ubuntu-desktop
```

Doing so with 9.10, although not impossible, might have its challenges, since it's past its "use by" date (see [here]("https://wiki.ubuntu.com/Releases")). You always have the option of installing a newer version: don't forget to make backups of important data first!

---

### Post by Greg Roberts on 2012-10-29
Thanks
 
Can you comment if Ubuntu hasa concept of an upgrade or is it always a fresh install ?

---


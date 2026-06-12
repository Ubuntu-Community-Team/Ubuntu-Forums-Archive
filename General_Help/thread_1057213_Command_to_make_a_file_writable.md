---
title: "Command to make a file writable?"
date: 2009-02-01
forum: General Help
---

### Post by BlkTwilight on 2009-02-01
(First post. Woo. Also, if this happens to be the wrong catagory...well, my bad.)

Since there has to be a command for this, what's the command for making a read-only file writable? I need it becuase I'm trying to change my default window manager back to Gnome, since I can't get X to start, but the file containing that precious setting? Read-only.

Anyway, thanks in advance.

---

### Post by x1a4 on 2009-02-01
```
chmod u+w *file*
```
will give the owner of *file* the permission to write to it.

```
chmod gu+w *file*
```
will give the owner and group of *file* permission to write to it.

see ```
chmod --help
``` and ```
man chmod
``` for more information.

---

### Post by BlkTwilight on 2009-02-01
Thanks!

As for my little X issue, I got it working. Thank you failsafe backup xorg.conf file!

---


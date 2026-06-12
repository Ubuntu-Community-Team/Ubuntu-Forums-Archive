---
title: "Rsync Problem"
date: 2009-06-06
forum: General Help
---

### Post by LIB53 on 2009-06-06
I having a problem using rsync because i'm trying to sync with a FreeAgent Drive, and the mount point has a space in it. The exact mount point is "/media/FreeAgent Drive". Is there a way to use this directory in terminal?

---

### Post by Rocket2DMn on 2009-06-06
You could wrap the path in quotes, or put \ before the space (it's called an escape character).
"/media/FreeAgent Drive"
/media/FreeAgent\ Drive

Using the escape character might not work if rsync is expecting more arguments to follow.  Alternatively, you could change the label on the USB drive to something more personalized, and without a space in it.  See [uhelp]community/RenameUSBDrive[/uhelp].

---

### Post by LIB53 on 2009-06-06
The Quotes trick seems to have worked. It's still going. Quite a bit to back up. lol. This is the command i used:

$ rsync –av /home/me "/media/FreeAgent Drive/me"

Quotes didn't work on the home/me part. I don't know why, but the command is working so it's not an issue. Thanks for the help. Really appreciate it.

---


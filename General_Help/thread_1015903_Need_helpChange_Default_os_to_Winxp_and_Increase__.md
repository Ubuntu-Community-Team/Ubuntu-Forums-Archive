---
title: "Need help:Change Default os to Winxp and Increase  time out"
date: 2008-12-19
forum: General Help
---

### Post by deepakbm on 2008-12-19
How can i change the default os to winxp and increase time out please help

---

### Post by dorkdork777 on 2008-12-19
Install QGrubEditor or Startup-Manager. Both let you do this easily. :)

---

### Post by Agent Smith on 2008-12-19
I increased my timeout by going to /boot/grub/menu.lst and just changed the timeout to 10 instead of 3 seconds. I had to do it as root or i couldnt save the changes.

---

### Post by ajcham on 2008-12-19
Use...

```
gksu gedit /boot/grub/menu.lst
```

...to open the file for editing.

These are the lines you are interested in:

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3
```

The default number should be the number where the Windows option appears in the Grub menu, minus 1 (because the count starts from 0).  So if Windows is the third option, change the line to:

```
default		2
```

Timeout is self-explanatory.

---

### Post by deepakbm on 2008-12-19
Thanks A lot



> **ajcham said:**
> Use...

```
gksu gedit /boot/grub/menu.lst
```

...to open the file for editing.

These are the lines you are interested in:

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3
```

The default number should be the number where the Windows option appears in the Grub menu, minus 1 (because the count starts from 0).  So if Windows is the third option, change the line to:

```
default		2
```

Timeout is self-explanatory.

---


---
title: "Shortcut Icons on Desktop"
date: 2010-09-13
forum: Desktop Environments
---

### Post by felixvah on 2010-09-13
How would I create a command line (batch) on Ubuntu 9.10 desktop?  For example, I go to terminal and type in $sudo /etc/init.d/gdm restart to restart gdm.  Instead of having to type in the line every time, how could I write the line in to a batch file and create a short to the desktop to avoid to type in the command every time.

I can do a .bat in Windows, but I don't know how to do it in Ubuntu.  Can anyone help?

---

### Post by kerry_s on 2010-09-13
right click the desktop & create a file
put:
```
#!/bin/bash
your first command
next command
etc...
exit 0

```

save it, right click the file-> properties-> permissions, check the execute

all done just double click on it.

---

### Post by felixvah on 2010-09-16
thanks, I'll try that.. Do where do I need to store the usename and password?  If i'm going to specify sudo than I would need a password right?

---

### Post by kerry_s on 2010-09-16
> **felixvah said:**
> thanks, I'll try that.. Do where do I need to store the usename and password?  If i'm going to specify sudo than I would need a password right?

use "gksudo" so you can type in the password.
or
you can use the "NOPASSWD:" in sudoers for the program's.

---

### Post by kerry_s on 2010-09-17
> **JaredJay said:**
> The word icon is normally placed in the start menu under programs, just  right click on it and select send to then desktop create shortcut.

no, he's creating a laucher that launches several programs instead of 1, it's not in the menu.

---

### Post by Gaygerbil on 2010-09-18
You can just make the command a keyboard shortcut also which is much simpler, just create a new shortcut and then put in that command in the command box and assign it to a keybinding...bam done.

---


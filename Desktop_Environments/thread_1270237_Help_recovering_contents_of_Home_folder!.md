---
title: "Help recovering contents of Home folder!"
date: 2009-09-19
forum: Desktop Environments
---

### Post by Johny79 on 2009-09-19
I tried setting up a second screen and the whole system froze, now I'm in endless loop failed disk checks & restarts and having spent a couple of hours on this and got nowhere I figured a reinstall was in order :(

I need to urgently recover some files from my Home folder so I figured I'd use the Live CD but it says I don't have permission to copy the files!?

Any ideas? I really really need those files ASAP otherwise in serious trouble! :(

---

### Post by sharkbite1414 on 2009-09-19
have you tried:
> sudo nautilus

---

### Post by jerrrys on 2009-09-19
thats one way to do it, but i believe thats **gksudo nautilus**

---

### Post by gnudoc on 2009-09-19
gksu, gksudo and sudo will all work. There are subtle and not-so-subtle differences, but they will all work.

---

### Post by Johny79 on 2009-09-19
For future reference "sudo nautilus" didn't work, it still said that it didn't have permission.

I'm guessing it's because running as root on the Live CD doesn't give you root privileges over the file system on the systems hard drives.

Anyway, luckily I managed to fix it in the end by restoring from a recent system backup (leaving most of the home folder untouched), first time I've had to do that and thankfully it went well! :)

---


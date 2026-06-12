---
title: "lock screen from command line"
date: 2008-12-13
forum: Desktop Environments
---

### Post by leptogenesis on 2008-12-13
I'm trying to lock the screen from the command line.  I've tried two commands that I've found in other threads, but neither works:

```

leptogenesis@leptogenesis-laptop:~$ dcop kdesktop KScreensaverIface lock
call failed
leptogenesis@leptogenesis-laptop:~$ kdesktop_lock
bash: kdesktop_lock: command not found

```

What should I use to lock the screen in KDE4?

---

### Post by leptogenesis on 2008-12-13
Finally found it:

```

qdbus org.freedesktop.ScreenSaver /ScreenSaver Lock

```

---

### Post by mtibbits on 2011-02-04
Thank you!!! That was exactly what I've been searching for!

---


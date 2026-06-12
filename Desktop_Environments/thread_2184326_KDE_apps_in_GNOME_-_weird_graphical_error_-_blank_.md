---
title: "KDE apps in GNOME - weird graphical error - blank window"
date: 2013-10-28
forum: Desktop Environments
---

### Post by pasogo91 on 2013-10-28
Hello! First time posting here!

So I have an Ubuntu Server 12.04, which was recently messed up.

Everything is almost OK now, but I have some KDE apps installed which I used to control just fine and now I can't.

If I execute the app normally, I can operate it. If I open them with "gksu" or "kdesudo" (I need to control some apps as root) I get a blank window, like there is some sort of problem with the graphics.

If I open a graphic root session the error is not present, and I can use the apps, but since I'm trying to "repair" my server from it's recently errors, I want to do what I used to do, to use those apps the way I did.

I'm guessing some libraries or configs may be wrong or not present at all, but no idea of what to do.

Can anyone help me?

Thanks!

---

### Post by pasogo91 on 2013-11-02
No one? Please, I don't know what other package I may need to install...

EDIT

Some extra info if I run the app from the terminal:

```
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x3e0005b
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x3e0005b
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x3e0005b
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x3e0005b
kuser(11554)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x3e0005b
X Error: BadShmSeg (invalid shared segment parameter) 128
  Extension:    129 (MIT-SHM)
  Minor opcode: 2 (X_ShmDetach)
  Resource id:  0x3e0005a
```

---


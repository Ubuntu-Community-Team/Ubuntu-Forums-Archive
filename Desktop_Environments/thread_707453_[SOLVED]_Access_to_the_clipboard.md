---
title: "[SOLVED] Access to the clipboard"
date: 2008-02-25
forum: Desktop Environments
---

### Post by tplng on 2008-02-25
Yes, thats it. Is there a way to get the content of the clipboard and copy it to a file? Or, if possible, that would be better, is it possible to get the contents directly from an C application?

I'm using GNOME.

---

### Post by jeffus_il on 2008-02-25
There's a package called glipper in the repository, I haven't used it, it claims to do what you need, otherwise there's klipper from KDE which is good, but that will drag a lot of KDE libraries with it, if that doesn't bother you.

---

### Post by tplng on 2008-02-25
Thanks, I'll try it out :)

---

### Post by tplng on 2008-02-25
Ehm, no, none of this do this, what i want. To copy the contents of the GNOME- Clipboard to a file, or even better, to a C- Application.

---

### Post by GeneralZod on 2008-02-25
klipper, at least, provides a dcop interface that allows you to get or set the contents from the command-line (or from exec()ing from a C program, or using dcop bindings, or ...).  Worst case, you can grab the source and find out how it does this :)

---

### Post by tplng on 2008-02-25
Oh thanks, reading the source was not necessary, I have found it out myself :D . Thank you very, very much!

---


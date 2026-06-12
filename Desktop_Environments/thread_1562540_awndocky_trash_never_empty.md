---
title: "awn/docky trash never empty"
date: 2010-08-27
forum: Desktop Environments
---

### Post by rafaellaguna on 2010-08-27
Look at the screenshot, I have only one file in trash but AWN and Docky counts 47+1 items. When it's empty it counts 47, and there's no way to really empty. But files are really gone. It doesn't happens with Cairo Dock (I don't know why).

Can anyone help me?

[IMG]http://dl.dropbox.com/u/133108/captura.png[/IMG]

---

### Post by rafaellaguna on 2010-08-27
Sorry, I discovered it by myself. Just did this:

sudo rm -rf ~/.local/share/Trash

rebooted and everything's fine.

---


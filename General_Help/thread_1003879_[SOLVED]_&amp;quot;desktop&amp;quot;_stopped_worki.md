---
title: "[SOLVED] &amp;quot;desktop&amp;quot; stopped working, folders hidden, cant right click"
date: 2008-12-06
forum: General Help
---

### Post by spandanj on 2008-12-06
Ubuntu 8.04


My desktop for some reason stopped working. I cannot do the following any longer:::

1) can't right click
2) all the desktop icons/folders are missing.

even though the folders are there in nautilus

So, How do I get it back?

---

### Post by dyous87 on 2008-12-06
Did you try logging out and back in or restarting your computer?

If you want to try this first open up a terminal and type:
```
metacity --replace
```

I think that should work.

You can also try hitting "ctrl, alt, backspace" to restart you x server.

David

---

### Post by Flimm on 2008-12-06
Try running nautilus.
Also, you might have accidentally disabled the desktop in gconf, here's the gconf key:
/apps/nautilus/preferences/show_desktop
Run gconf-editor to get to it.

---

### Post by spandanj on 2008-12-06
solved...


did the gconf-editor-->nautilus-->desktop.....it was already selected.

Restarted computer.

That solved it.

thanks

---


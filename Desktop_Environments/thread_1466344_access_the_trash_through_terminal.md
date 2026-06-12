---
title: "access the trash through terminal"
date: 2010-04-30
forum: Desktop Environments
---

### Post by someone235 on 2010-04-30
I want to write a script that is messing with the trash, but i dunno how to access it.
i tried ~/.Trash or ~/.trash , and it didnt work, so how can i access it?

---

### Post by antenna on 2010-04-30
Try ~/.local/share/Trash/files/

---

### Post by sisco311 on 2010-04-30
You can use the trash, list-trash, restore-trash and empty-trash commands from the [trash-cli]("apt://trash-cli") package.

EDIT: for the location of the trash, check out the FreeDesktop.org Trash Specification:
[http://www.freedesktop.org/wiki/Specifications/trash-spec](http://www.freedesktop.org/wiki/Specifications/trash-spec)

---


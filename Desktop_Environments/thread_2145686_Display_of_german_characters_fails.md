---
title: "Display of german characters fails"
date: 2013-05-16
forum: Desktop Environments
---

### Post by schneitzmaster on 2013-05-16
Hi Forum,
my administrator changed something in the locale and now all my special characters like ä ö ü ß are displayed as a box with an X. (see attached picture)
Does anyone know how to fix this?
cheers

[ATTACH=CONFIG]242639[/ATTACH]

---

### Post by schneitzmaster on 2013-05-16
Hi solved it my self
i had to change the /etc/environmentfile

--> LC_ALL = "de_DE:UTF-8"

---


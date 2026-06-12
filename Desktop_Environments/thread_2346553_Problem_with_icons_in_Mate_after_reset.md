---
title: "Problem with icons in Mate after reset"
date: 2016-12-16
forum: Desktop Environments
---

### Post by yanunim95 on 2016-12-16
I got strange problem with icons.
It happened after accidental reset.
[IMG]https://i.stack.imgur.com/BMYw7.png[/IMG]


This pink color is everywhere.
In dialogs, menus.

Changing icons theme in mate brings make new icons also pink.
Also changing of  desktop theme makes icons pink.
In ```
/usr/share/icons
``` all icons looking normal.


How can I get normal colors in system?

[LIST]
[*]OS: Ubuntu 16.04
[*]Mate: default
[/LIST]

---

### Post by yanunim95 on 2016-12-16
Small Update.
Same happens with guest sessions.

---

### Post by yanunim95 on 2016-12-17
Solved.

It is problem with oibaf drivers.
After purging ppa from system icon colors are ok now.

---


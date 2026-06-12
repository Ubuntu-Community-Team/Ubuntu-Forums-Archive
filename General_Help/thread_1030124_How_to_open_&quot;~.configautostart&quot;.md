---
title: "How to open &quot;~/.config/autostart&quot;"
date: 2009-01-04
forum: General Help
---

### Post by cayenne on 2009-01-04
Hi!
I was wondering if anybody could show me the right command to open "~/.config/autostart" in jed or nano from the terminal.

Thanx!

---

### Post by nothingspecial on 2009-01-04
.config/autostart is a directory so

```
cd .config/autostart
```to enter it

```
ls
``` to see what`s in it

for example ```
pidgin.desktop
``` is in mine
```

cat pidgin.desktop
``` to view it
```

nano pidgin.desktop
``` to edit it

---


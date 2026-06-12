---
title: "gnome-btdownload on port 6881"
date: 2007-05-28
forum: Desktop Environments
---

### Post by finite9 on 2007-05-28
I try to download files from supertorrent.org but it keeps complaining that port 6881 is blacklisted.  I edited the commandline of the gnomebtdownload entry in the menu so that it reads:

```
gnome-btdownload -minport 52150 -maxport 52159
```

but I still get the error.  I do not get this with other bittorrent sites.  Any ideas whats going on?

---

### Post by finite9 on 2007-05-29
never mind.  it was because I had cut and pasted the text from OOo and it 'converted' the --minport to one minus sign '-minport' and as a consequence, defaulted to 6881 as it didnt recognise the switch.

---


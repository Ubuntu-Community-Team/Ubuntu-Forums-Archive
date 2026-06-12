---
title: "Gedit not in the launcher - unbelievable!"
date: 2013-01-06
forum: Desktop Environments
---

### Post by HughJarse on 2013-01-06
I can't understand why gEdit is not in the launcher and find this even more frustrating as you can't drag and drop a shortcut for it.

ubuntu 12.04 LTS

---

### Post by howefield on 2013-01-06
If you can't drag the icon to the launcher, open gedit and right the launcher icon and select "Lock to Launcher".

---

### Post by mc4man on 2013-01-06
In a quick test works fine here adding gedit to launcher though gedit.desktop has some issues in the launcher with the supplied quicklists

The "Open a New Document" quicklist is using the wrong command, not yet fixed in 12.04, maybe never will be.

user side fix - (you can use just sudo if desired & won't see extra docu opened
```
gksudo gedit /usr/share/applications/gedit.desktop

```
In [Desktop Action Document] change the Exec= to 
```
Exec=gedit --new-document
```

There also may be an issue with how the "Open a New Window" quicklist works, didn't pursue as really don't use 12.04

---

### Post by Chogan on 2013-01-06
open gedit and then right click on it's icon in launcher and select "lock to launcher".

---

### Post by niekn on 2013-01-06
does it come up in the dash?
if not, install alacarte and search the dash for "alacarte" it will come up with something like "main menu" there you can create new launchers easily.
the launchers will come up in the dash.

---


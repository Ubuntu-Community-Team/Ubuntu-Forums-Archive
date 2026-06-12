---
title: "How do I fix my configuration?"
date: 2009-04-30
forum: Desktop Environments
---

### Post by camper365 on 2009-04-30
I ran the following commands:
```
gconftool-2 --type string --set /apps/nautilus/preferences/show_desktop 'false'
sudo gconftool-2 --type string --set /apps/nautilus/preferences/show_desktop 'false'

```
and I was no longer able to access the files on my Desktop.
What I was trying to do was enable the multiple wallpapers on my Desktop Cube, but it didn't work.
How do I fix it?
I have already run
```
gconftool-2 --type string --set /apps/nautilus/preferences/show_desktop 'true'
sudo gconftool-2 --type string --set /apps/nautilus/preferences/show_desktop 'true'

```
in an attempt at reversing what I had done, but it didn't work.

---

### Post by Tavarid on 2009-04-30
I think I see your problem here, try running it like this:

gconftool-2 --type **bool** --set /apps/nautilus/preferences/show_desktop 'true'
sudo gconftool-2 --type **bool** --set /apps/nautilus/preferences/show_desktop 'true'

---

### Post by camper365 on 2009-05-01
It worked, but now I can't use the Compiz Wallpaper feature.

---


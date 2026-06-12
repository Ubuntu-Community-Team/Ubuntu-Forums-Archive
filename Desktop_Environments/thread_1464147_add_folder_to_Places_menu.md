---
title: "add folder to Places menu"
date: 2010-04-27
forum: Desktop Environments
---

### Post by mathfeel on 2010-04-27
By default, xdg-user-dirs defines the following directories:
```
cat /etc/xdg/user-dirs.defaults 
# Default settings for user directories
#
# The values are relative pathnames from the home directory and
# will be translated on a per-path-element basis into the users locale
DESKTOP=Desktop
DOWNLOAD=Downloads
TEMPLATES=Templates
PUBLICSHARE=Public
DOCUMENTS=Documents
MUSIC=Music
PICTURES=Pictures
VIDEOS=Videos
```

Under "Places" on the panel, I want to add "Downloads" to it.  How do I do that?

Thanks,

MZ

---

### Post by Cygnia on 2010-04-27
Just drag the Downloads Folder to the side panel in Nautilus and it's added to your Bookmarks, and will then appear in the Places menu.

---

### Post by mathfeel on 2010-04-27
I see, so the Place menu is not automatically populated by the system but manually populated by the user?

---

### Post by Cygnia on 2010-04-27
A default install comes with a stock selection of entries, to which you can add or remove as you wish.

---

### Post by mathfeel on 2010-04-28
Is it possible to associate new user-dirs? For example, can I make something like ~/Works have the same icon as ~/Documents, which is XDG_DOCUMENTS_DIR?

---


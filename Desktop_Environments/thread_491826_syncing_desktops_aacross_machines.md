---
title: "syncing desktops aacross machines"
date: 2007-07-04
forum: Desktop Environments
---

### Post by jamaas on 2007-07-04
Could someone please tell me what files I need to copy from one machine to another to get the same settings for gnome/panels/desktop etc?  I have one well configured and like it, and my notebook disk died, so with reinstall would like to copy settings from the desktop that works well across to my notebook.

Both are running updated gnome on 7.04.   Thanks for any/all suggestions.

Jim

---

### Post by hikaricore on 2007-07-04
Well to be honest all of your settings are stored in your home directory.

If you made an archive of your entire home directory, you could copy it over and extract it on the other machine, it should turn out exactly the same as you remember it.

```

cd Desktop
tar cvpzf copy.tgz ~
```

^ Would make an archive of your entire home folder and place it on your desktop named copy.tgz

---

### Post by aquavitae on 2007-07-04
Not entirely certain of the exact files for gnome, but they will be in a hidden folder in your home directory, probably something like ~/.gnome and ~/.gtk.  All the user settings are stored in hidden folders under the home directory, so you could just copy all of them and keep other settings too (e.g. gstreamer, firefox,...)

---


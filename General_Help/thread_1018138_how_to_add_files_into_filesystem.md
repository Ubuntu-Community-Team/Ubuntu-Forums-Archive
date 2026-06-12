---
title: "how to add files into filesystem?"
date: 2008-12-21
forum: General Help
---

### Post by Howitzer777 on 2008-12-21
I need to add a folder to the /usr/share/themes but it says i don't have the right priliages. helP


gtk theme

---

### Post by jerome1232 on 2008-12-21
If your just installing a gtk theme (and it's downloaded as a *.tgz or .tar.gz file) then you should just be able to install it like this

System-Preferences-Appearance-Theme tab, drag the file and drop it in.

IF that doesn't work and your account is an admin on this machine then you can do it with sudo.


```
# adding a folder
sudo mkdir /usr/share/themes/newfolder
# copying a folder/file
sudo cp /path/to/source/folder/or/file /usr/share/themes
```

Or if you aren't comfy with the command line you can run nautilus as root, exercise caution as you can easily destroy your system with a stray delete key.

press alt+f2, type 'gksu nautilus' without the quotes. When deleting things in this mode deleted items will goto roots trash not yours so be mindful of that if you delete large files while running nautilus as root (You can hold shift to bypass the trash)

---


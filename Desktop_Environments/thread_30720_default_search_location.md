---
title: "default search location"
date: 2005-04-29
forum: Desktop Environments
---

### Post by 23meg on 2005-04-29
is it possible to change the default location to be searched in nautilus's search dialog? it defaults to the home folder, and i'd rather have it set to filesystem by default, since i generally tend to look for things all over the system..

---

### Post by Xerampelinae on 2005-04-30
[QUOTE=23meg]is it possible to change the default location to be searched in nautilus's search dialog? it defaults to the home folder, and i'd rather have it set to filesystem by default, since i generally tend to look for things all over the system..[/QUOTE]
 ```

gnome-search-tool --path=/

```

---

### Post by 23meg on 2005-05-03
thanks. is there a config file i can tweak to set the default search path? i need this because i have a keybinding that launches gnome-search-tool without command line options, and the "search for files" entry in the places menu can't be tweaked to enter this parameter.

---


---
title: "how do i edit esd.conf?"
date: 2005-04-29
forum: Desktop Environments
---

### Post by kisain on 2005-04-29
need to edit esd.conf so i can run teamspeak plz help

---

### Post by XDevHald on 2005-04-29
[QUOTE=kisain]need to edit esd.conf so i can run teamspeak plz help[/QUOTE]
 You'll need to **sudo gedit **then the directory that the file is in then add the file at the end of the command.

**Example: **sudo gedit /etc/apt/sources.list <---This is what it should look like when trying to open a file to edit it in gedit :) Just replace the text with your directory and file name at the end.

**Edit$ ~ **[http://www.ubuntuforums.org/showthread.php?t=24008&page=1](http://www.ubuntuforums.org/showthread.php?t=24008&page=1)

The above link will also give you an easy setup with the drag&drop to your taskbar to edit files without doing the gedit command :) Enjoy

---

### Post by bilal.17 on 2008-03-29
> **kisain said:**
> need to edit esd.conf so i can run teamspeak plz help

```
 gksudo gedit /etc/esound/esd.conf
```

---


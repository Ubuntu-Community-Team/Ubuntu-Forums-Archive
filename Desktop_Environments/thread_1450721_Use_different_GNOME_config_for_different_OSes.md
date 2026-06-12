---
title: "Use different GNOME config for different OSes"
date: 2010-04-09
forum: Desktop Environments
---

### Post by Tipo on 2010-04-09
I have a mixed environment of Ubuntu and CentOS machines in which I use network accounts.

The problem is that gnome stores all it's settings in the .gnome folders, and then you've logged into one OS and saved your GNOME settings, logging into the other OS results in missing menus and other oddities with the gnome-panel.

Is there a way for me to define a different location for my Ubuntu machines to store gnome configurations? Something like ~/.gnome_ubuntu?

---

### Post by Tipo on 2010-04-09
To answer my own question:

On my Ubuntu machines, I need to edit ```
/etc/gconf/2/path
```

In that file, just change ```
xml:readwrite:$(HOME)/.gconf
``` to ```
xml:readwrite:$(HOME)/.gconf_ubuntu
```

Works like a charm \\:D/

---


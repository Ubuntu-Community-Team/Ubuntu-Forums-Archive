---
title: "not enough permissions to enable desktop effects"
date: 2008-04-20
forum: Desktop Effects &amp; Customization
---

### Post by wildman4god on 2008-04-20
i am trying to enable my desktop effects on my dell Latitude D600 with an ATI Radeon mobility 9000 graphics card and i have tried the things other people have done in this forum but part way through i get not enough permissions it usually when i have to write new files to the x11 folder, it will not let me save changes to the configuration either which i need to do. someone please help me.

---

### Post by rune0077 on 2008-04-20
Because you need to have root-permission to write to anything outside your own homefolder. To open and edit the files in X11 (or anywhere else outside of home), use this command from a terminal:

```
sudo gedit <NameOfFile>
```

Where NameOfFile is the full path of the file you want to edit (for instance, /etc/X11/xorg.conf).

The "sudo" part means you'll do the operation with root-permission, and will prompt you for your password.

---


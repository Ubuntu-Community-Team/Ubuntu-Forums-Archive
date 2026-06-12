---
title: "xfer files between users"
date: 2005-05-04
forum: Desktop Environments
---

### Post by sage on 2005-05-04
How can I xfer files (ie drag and drop) between users using Nautilis or Konqueror using sudo instead of having to log in as root?

---

### Post by nad on 2005-05-04
Have three windows open; source directory, parent of target directory and a terminal.

Type the command: sudo cp -p  in the terminal window, drag and drop the file from the source window, drag and drop the parent directory from the target window, backspace and add: /.  to the target path and issue the command.

The 'p' switch maintains permissions. Depending on what the second user wishes to do with the file, you may need to adjust this, but as the owner you can do this from the files' property window.

---

### Post by shakin on 2005-05-04
Open Nautilus with sudo:

```

$ sudo nautilus

```

It might be useful to create a menu item that does this. For that, use gksudo instead of sudo so it opens a Gnome password box for the password.

---

### Post by sage on 2005-05-04
thank you, "sudo nautilus" works prefectly and is so easy.

---


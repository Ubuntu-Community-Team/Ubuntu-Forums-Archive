---
title: "Gnome configuration editor file"
date: 2008-05-14
forum: Desktop Environments
---

### Post by wrgb2 on 2008-05-14
Is there a single file that correlates to the Gnome Configuration editor?  I want to make some changes, but would like to back up the current configuration just to be safe.

---

### Post by wrgb2 on 2008-05-14
Bump. Anyone know the answer to this?
Thanks,

---

### Post by sdennie on 2008-05-14
Have a look in ~/.gconf.  The files are organized like in gconf-editor there and are just plain xml files.

---

### Post by Pipps on 2008-12-23
Has anyone found an answer to this gconf backup question? I would be very interested to learn of a solution as well. It would be really useful to me. Thanks.

---

### Post by Pipps on 2008-12-23
May suggest to anyone who might be interested, that you navigate to the following directory:

/home/[username]/.gconf/apps/metacity

And potentially just copy and paste the 'global_keybindings' and 'keybinding_commands' folders, with their individual '%gconf.xml' files, to a backup directory.

Please feed-back if this works for anyone!

---


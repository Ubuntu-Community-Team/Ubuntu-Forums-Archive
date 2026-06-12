---
title: "Cant add a script to bin - Do not have permission"
date: 2009-03-01
forum: General Help
---

### Post by phr33k-dc on 2009-03-01
tried to put a script in here but a message came up saying i dont have permission. /home/david-dc/bin/

'Permission Denied'

How do i put the script in?

---

### Post by phr33k-dc on 2009-03-01
any ideas?

---

### Post by Rallg on 2009-03-01
That particular bin folder is in your Home directory, rather than in a system directory. Right-click the folder, get the properties, and find out who owns it (permissions).

If you (david-dc) own it, then you should be able to change the permissions.

If it is owned by root (or someone else), then you probably need to change the owner to be yourself. You can do that via Terminal as root, or you can do it through your system's file manager. In Ubuntu (not Kubuntu or Xubuntu), the name of the file manager is nautilus. So go to Terminal:

sudo nautilus

After it gets your password, a file manager window will open (in some cases, you might have to use "gksudo nautilus" instead). Navigate upwards to the top level, then down into your home directory. Right-click the bin folder, and get its properties. Now you will have the authority needed to change the owner, and also change who can do what.

---


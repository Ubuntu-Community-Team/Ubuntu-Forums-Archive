---
title: "odot GTK error / evolution IMAP PIM's"
date: 2005-09-20
forum: Desktop Environments
---

### Post by Marc Higgins on 2005-09-20
trying to find a replacement for evolution because well it sucks & crashes with large (+1g) imap files, (it seems to do this on redhat, mandrake, deb & ubuntu) 

thunderbird is a great mail client but, the plugin cal/task is a very poor pim, so in the search for a pim i thought i would try ODOT the task manager,

Have installed & checked the dependencies but when i fire either as a normal user or sudo i get the following gtk error


~$ odot
Use of uninitialized value in string ne at /usr/bin/odot line 1963.
*** unhandled exception in callback:
***   Gtk-ERROR **: file gtktreestore.c: line 581 (gtk_tree_store_get_path): assertion failed: (G_NODE (iter->user_data)->parent != NULL) at /usr/bin/odot line 1975.
***  ignoring at /usr/bin/odot line 1358.

Would appreciate it if anyone could help with my evolution problems, my odot problem or even sugest a new PIM

---


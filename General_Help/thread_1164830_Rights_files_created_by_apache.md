---
title: "Rights files created by apache"
date: 2009-05-20
forum: General Help
---

### Post by mech7 on 2009-05-20
Somehow the files that apache creates I can't move them on my samba share... i can change directories though... Is there anyway to change the default rights on how apache creates them.

---

### Post by mb_webguy on 2009-05-20
I'm not sure what you mean...  The only files Apache would "create" would be its configuration and log files.  You can copy these from the terminal by using "sudo cp /path/to/file /path/to/target", change their ownership with "sudo chown user:group /path/to/file".  You can do these things in Nautilus by opening the run dialog or terminal and enter the command "gksu nautilus".

---

### Post by ActiveFrost on 2009-05-20
If you want to move/edit protected files, use sudo. Instead of using CLI, launch *_sudo nautilus /var/_* ( which will open you a file browser ).

---


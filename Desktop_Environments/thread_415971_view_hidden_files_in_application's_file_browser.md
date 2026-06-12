---
title: "view hidden files in application's file browser"
date: 2007-04-20
forum: Desktop Environments
---

### Post by raptor2552 on 2007-04-20
Hello

Is there a setting some where that I can change to have all applications file browser show hidden files without typing a (dot) in the location bar? I've looked around using gconf-editor and found key: desktop->gnome->file_views->show_hidden_files checked. Maybe there is a key I need to add? There many guides for Nautilus, which works fine, but I haven't found anything for the file browser used by the applications.

Feisty 7.04 (Most excellent; OS Rex)

Thanks

---

### Post by ardchoille42 on 2007-04-20
> **raptor2552 said:**
> Hello

Is there a setting some where that I can change to have all applications file browser show hidden files without typing a (dot) in the location bar? I've looked around using gconf-editor and found key: desktop->gnome->file_views->show_hidden_files checked. Maybe there is a key I need to add? There many guides for Nautilus, which works fine, but I haven't found anything for the file browser used by the applications.

Feisty 7.04 (Most excellent; OS Rex)

Thanks

Open nautilus. Go to Edit -> Preferences. In the File Management Preferences dialog, check the "Show hidden and backup files" checkbox in the View tab and restart nautilus. As far as I know, there isn't a way to have hidden files appear in the Open/Save dialogs of applications.

---

### Post by s_p_a_r_k_y on 2007-04-20
you can also in any open nautilus window press ctrl-h and it toggles on and off hidden file viewing

---

### Post by raptor2552 on 2007-04-20
Nautilus works OK and I have it set to show all files. Gedit shows hidden files in the sidebar file browser. It's other applications Save/Open dialogue that I'm asking about

Thanks

---

### Post by s_p_a_r_k_y on 2007-04-20
the ctrl-h method works in the save/open dialog.

---

### Post by RedSquirrel on 2007-04-20
In the save/open dialog, try right-clicking in the area where your directories and files are displayed. There should be a checkbox for  "show hidden files" or something similar.

---

### Post by raptor2552 on 2007-04-20
> **RedSquirrel said:**
> In the save/open dialog, try right-clicking in the area where your directories and files are displayed. There should be a checkbox for  "show hidden files" or something similar.

Yeah that's good. Anyway to turn this feature on permanently?

Edit: never mind it leaves it checked, silly me

---

### Post by RedSquirrel on 2007-04-20
I think it saves it each time. So if you do it once, it should keep that setting until you change it back to NOT display hidden files.

---


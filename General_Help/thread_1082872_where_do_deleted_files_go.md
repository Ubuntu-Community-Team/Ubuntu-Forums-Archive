---
title: "where do deleted files go?"
date: 2009-02-28
forum: General Help
---

### Post by sunder10 on 2009-02-28
Does ubuntu have some sort of recycle bin where deleted files go to? Because I don't want those deleted files clogging up my space

Thanks

---

### Post by cb951303 on 2009-02-28
it goes to /home/USERNAME/.local/Trash

personally I add the trash applet to my panel (it should be there by default), you can right click and empty it. also you can drag and drop files to this icon

you can also show the trash icon in desktop, in order to do that: run "gconf-editor" > Apps > Nautilus > Desktop > Check trash_icon_visible

---

### Post by fjgaude on 2009-02-28
Yes, the Trash icon should be in the panel, if not you can add it. Right click the plan and click Add to Panel to see what can be added, lots.

---

### Post by Old *ix Geek on 2009-02-28
It depends on HOW you're deleting them.  If you're deleting them from a command line with "rm"--they're gone.  Period.  If you're doing it with a GUI but have set your preferences to bypass the trash can, they're gone. Otherwise, they're in your trash can.

---

### Post by ulfj on 2009-02-28
so they are in your trash even if you empty the trashcan? I thought that when you emptied the trash they are gone and not taking up space.sorry if I missed something but got my 1rst cup of coffee going now.

---

### Post by Vaphell on 2009-02-28
he meant that:
1. using rm command kills file permanently, no trashcan involved
2. removing file with SHIFT+DEL kills file permanently, no trashcan involved
3. you can configure context menu to allow permanent removal (in nautilus preferences), no trashcan involved 
4. in any other case trashcan needs purging

---


---
title: "Can't delete locked photo folder"
date: 2009-01-01
forum: General Help
---

### Post by pennys on 2009-01-01
I'm a Ubuntu beginner and need help. I copied a folder of pics to my Ubuntu PC that originated from my WinXP PC via a CD. They reside in "/home/penny/Pictures".  I have attempted to delete or trash that folder to no avail.  It has a "padlock" icon next to the folder.  I tried to change the permissions of the "Access" files from "---" to "read and write" but that didn't work. When I clicked "Apply" all returned to "---"  How can I trash that folder?

---

### Post by dannytatom on 2009-01-01
try 

```

sudo chown -R penny:penny Pictures/

```

I think that's it, at least.

---

### Post by pennys on 2009-01-01
Thanks for the info but it didn't work.  I even tried restarting the computer to be sure the command was well and truly executed.  The folder is still locked.  Any other ideas?

---

### Post by drs305 on 2009-01-01
This will open nautilus and let you zap the Penny folder:
```

gksudo nautilus /home/penny/

```

Use SHIFT-Delete or the files will end up in root's trash, where a normal user can't delete them. Just be careful with Shift-Delete as there is no recovery from deleting the wrong folder!

---

